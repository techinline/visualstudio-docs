---
title: "IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3::EnumPersistedPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::EnumPersistedPorts"
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3::EnumPersistedPorts
This method retrieves an object that allows enumeration of the list of persisted ports.  
  
## Syntax  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### Parameters  
 `PortNames`  
 [in] A [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) structure that contains a list of port names to find and return among the persisted ports. Only those persisted ports with these names will be returned.  
  
 `ppEnum`  
 [out] An object that implements the [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) interface.  
  
## Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## Remarks  
 Persisted ports are loaded when a port supplier is instantiated, and saved when the port supplier is destroyed.  
  
## See Also  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)