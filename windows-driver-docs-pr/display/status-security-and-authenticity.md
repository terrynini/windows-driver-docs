---
title: Status Security and Authenticity
description: Status Security and Authenticity
keywords:
- status information WDK COPP
- status exchange WDK COPP
ms.date: 04/20/2017
---

# Status Security and Authenticity


## <span id="ddk_status_security_and_authenticity_gg"></span><span id="DDK_STATUS_SECURITY_AND_AUTHENTICITY_GG"></span>


**This section applies only to Windows Server 2003 SP1 and later, and Windows XP SP2 and later.**

The following figure shows an application requesting status messages from the video miniport driver, and then the video miniport driver sending the status messages to the application across the secure channel.

![diagram illustrating status exchange.](images/coppstus.png)

These status messages are contained in an envelope. The envelope contains data and MAC sections. The video miniport driver calculates the MAC of the status data by using the data integrity key and the OMAC. For more information about the MAC and OMAC, see [Cryptographic Primitives Used by COPP](cryptographic-primitives-used-by-copp.md).

The following table describes the values in the preceding figure.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Value</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>r<sub>APP</sub></p></td>
<td align="left"><p>128-bit random number generated by the application.</p></td>
</tr>
<tr class="even">
<td align="left"><p>STATUS</p></td>
<td align="left"><p>Variable-length status data.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MAC<sub>KDI</sub>(r<sub>APP</sub>, STATUS)</p></td>
<td align="left"><p>128-bit MAC of the status data using the data integrity session key.</p></td>
</tr>
</tbody>
</table>

 

 

 





