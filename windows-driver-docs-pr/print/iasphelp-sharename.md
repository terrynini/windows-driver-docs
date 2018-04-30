---
title: Iasphelp get\_ShareName method
author: windows-driver-content
description: The ShareName property enables an ASP Web page to obtain the printer's shared name.
MS-HAID:
- 'webfnc\_68b8e99e-a40b-44ee-94c8-2a8bcc293fa3.xml'
- 'print.iasphelp\_sharename'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fdb93613-9c7f-49ea-b90e-684b63e6417a
keywords: ["get_ShareName method Print Devices", "get_ShareName method Print Devices , Iasphelp interface", "Iasphelp interface Print Devices , get_ShareName method"]
topic_type:
- apiref
api_name:
- Iasphelp.get_ShareName
api_type:
- COM
---

# Iasphelp::get\_ShareName method


The **ShareName** property enables an ASP Web page to obtain the printer's shared name.

Syntax
------

```ManagedCPlusPlus
HRESULT get_ShareName(
  [out] BSTR *pVal
);
```

Parameters
----------

*pVal* \[out\]  
Caller-supplied pointer to a location to receive a pointer to a share name string.

Return value
------------

Win32 error codes can also be returned.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Return code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>S_OK</strong></td>
<td><p>The operation succeeded.</p></td>
</tr>
<tr class="even">
<td><strong>E_HANDLE</strong></td>
<td><p>The [<strong>Iasphelp::Open</strong>](iasphelp-open.md) method has not been called.</p></td>
</tr>
<tr class="odd">
<td><strong>E_OUTOFMEMORY</strong></td>
<td><p>Out of memory.</p></td>
</tr>
</tbody>
</table>

 

## <span id="ddk_iasphelp_sharename_gg"></span><span id="DDK_IASPHELP_SHARENAME_GG"></span>


### <span id="vbscript_example"></span><span id="VBSCRIPT_EXAMPLE"></span>VBScript Example

Remarks
-------

The [**Iasphelp::Open**](iasphelp-open.md) method must be called before the **Iasphelp::ShareName** property can be queried.

```
    Dim objPrinter, DrvrName
    strPrinter = Session("MS_printer")
    Set objPrinter = Server.CreateObject ("OlePrn.AspHelp")
    objPrinter.Open strPrinter
    DrvrName = objPrinter.ShareName
```

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Target platform</p></td>
<td>Desktop</td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td><p>Available in Windows 2000 and later versions of the Windows operating systems.</p></td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**Iasphelp::Open**](iasphelp-open.md)

 

 



