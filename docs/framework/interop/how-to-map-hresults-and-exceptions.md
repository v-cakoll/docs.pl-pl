---
title: "Porady: mapowanie wyników HRESULT i wyjątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41220f37837c1bd2e983a82ecb3406fe1cb918e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-map-hresults-and-exceptions"></a>Porady: mapowanie wyników HRESULT i wyjątków
Metody modelu COM raportów o błędach przez zwrócenie wyników HRESULT; metod .NET Raportuj je przez zgłaszanie wyjątków. Środowisko uruchomieniowe obsługi przejścia między nimi. Każda klasa wyjątków w programie .NET Framework mapuje HRESULT.  
  
 Klasy wyjątków zdefiniowanych przez użytkownika można określić, niezależnie od HRESULT jest odpowiedni. Te klasy wyjątków można dynamicznie zmieniać HRESULT, które mają być zwracane w przypadku wyjątku jest generowany przez ustawienie **HResult** na obiekt wyjątku. Dodatkowe informacje o wyjątku został dostarczony do klienta za pośrednictwem **IErrorInfo** interfejs, który jest zaimplementowany dla obiektu .NET w procesie niezarządzane.  
  
 W przypadku utworzenia klasy, która rozszerza **System.Exception**, należy ustawić podczas konstruowania pole HRESULT. W przeciwnym razie klasa podstawowa przypisuje wartość HRESULT. Nowe klasy wyjątku można mapować na istniejące HRESULT, podając wartości w Konstruktorze wyjątku.  
  
 Należy pamiętać, że czasami zignoruje środowiska uruchomieniowego `HRESULT` w przypadkach, gdy istnieje `IErrorInfo` obecne w wątku.  Problem ten może wystąpić w przypadku których `HRESULT` i `IErrorInfo` nie reprezentują tego samego błędu.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Tworzenie nowej klasy wyjątku i mapowanie go na HRESULT  
  
1.  Poniższy kod umożliwia utworzenie nowej klasy wyjątku o nazwie `NoAccessException` i mapowanie go HRESULT `E_ACCESSDENIED`.  
  
    ```cpp  
    Class NoAccessException : public ApplicationException  
    {  
        NoAccessException () {  
        HResult = E_ACCESSDENIED;   
    }  
    }  
    CMyClass::MethodThatThrows  
    {  
    throw new NoAccessException();  
    }  
    ```  
  
 Może wystąpić programu (w dowolnym języku programowania), który korzysta z kodu zarządzane i niezarządzane w tym samym czasie. Na przykład używa organizatora niestandardowego w poniższym przykładzie kodu **Marshal.ThrowExceptionForHR (int HResult)** metodę, aby zgłosić wyjątek, z określoną wartością HRESULT. Metoda wyszukuje HRESULT i generuje typ odpowiednich wyjątków. Na przykład HRESULT w poniższy fragment kodu generuje **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Poniższa tabela zawiera pełną mapowania z każdym HRESULT do jej klasy można porównywać pod względem wyjątek w programie .NET Framework.  
  
|HRESULT|Wyjątek .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**Appdomainunloadedexception —**|  
|**COR_E_APPLICATION**|**ApplicationException**|  
|**COR_E_ARGUMENT lub E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC lub ERROR_ARITHMETIC_OVERFLOW**|**Arithmeticexception —**|  
|**COR_E_ARRAYTYPEMISMATCH**|**Arraytypemismatchexception —**|  
|**COR_E_BADIMAGEFORMAT lub ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**Cryptographicexception —**|  
|**COR_E_DIRECTORYNOTFOUND lub ERROR_PATH_NOT_FOUND**|**Directorynotfoundexception —**|  
|**COR_E_DIVIDEBYZERO**|**Dividebyzeroexception —**|  
|**COR_E_DUPLICATEWAITOBJECT**|**Duplicatewaitobjectexception —**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException —**|  
|**COR_E_TYPELOAD**|**Entrypointnotfoundexception —**|  
|**COR_E_EXCEPTION**|**Wyjątek**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**Fieldaccessexception —**|  
|**COR_E_FILENOTFOUND lub ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST lub E_NOINTERFACE**|**Invalidcastexception —**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR_E_INVALIDFILTERCRITERIA**|**Invalidfiltercriteriaexception —**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**Invalidolevarianttypeexception —**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**IOException**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**Powstanie wyjątku MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**Missingfieldexception —**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**Missingmanifestresourceexception —**|  
|**COR_E_MISSINGMEMBER**|**Missingmemberexception —**|  
|**COR_E_MISSINGMETHOD**|**Missingmethodexception —**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**Multicastnotsupportedexception —**|  
|**COR_E_NOTFINITENUMBER**|**Notfinitenumberexception —**|  
|**E_NOTIMPL**|**Notimplementedexception —**|  
|**COR_E_NOTSUPPORTED**|**Notsupportedexception —**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY lub**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**Overflowexception —**|  
|**COR_E_PATHTOOLONG lub ERROR_FILENAME_EXCED_RANGE**|**Pathtoolongexception —**|  
|**COR_E_RANK**|**Rankexception —**|  
|**COR_E_REFLECTIONTYPELOAD**|**Wyjątku ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**Remotingexception —**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**Safearraytypemismatchexception —**|  
|**COR_E_SECURITY**|**SecurityException**|  
|**COR_E_SERIALIZATION**|**SerializationException**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**Stackoverflowexception —**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**Synchronizationlockexception —**|  
|**COR_E_SYSTEM**|**SystemException**|  
|**COR_E_TARGET**|**Targetexception —**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**Targetparametercountexception —**|  
|**COR_E_THREADABORTED**|**ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**Threadinterruptedexception —**|  
|**COR_E_THREADSTATE**|**Threadstateexception —**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException —**|  
|**COR_E_TYPEINITIALIZATION**|**Typeinitializationexception —**|  
|**COR_E_VERIFICATION**|**Verificationexception —**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Wszystkie inne wyników HRESULT**|**COMException**|  
  
 Aby pobrać rozszerzonych informacji o błędzie, zarządzanego klienta sprawdza pola obiekt wyjątku, który został wygenerowany. Dla obiekt wyjątku do dostarczające przydatnych informacji na temat błędu, należy zaimplementować obiektu COM **IErrorInfo** interfejsu. Środowisko wykonawcze używa informacji dostarczonych przez **IErrorInfo** zainicjować obiekt wyjątku.  
  
 Jeśli obiekt COM nie obsługuje **IErrorInfo**, środowisko uruchomieniowe inicjuje obiekt wyjątku z wartościami domyślnymi. Poniższa tabela zawiera każde pole skojarzona z obiektem wyjątków oraz identyfikuje źródło domyślne informacje, gdy obiekt modelu COM obsługuje **IErrorInfo**.  
  
 Należy pamiętać, że czasami zignoruje środowiska uruchomieniowego `HRESULT` w przypadkach, gdy istnieje `IErrorInfo` obecne w wątku.  Problem ten może wystąpić w przypadku których `HRESULT` i `IErrorInfo` nie reprezentują tego samego błędu.  
  
|Pole wyjątku|Źródło danych z modelu COM|  
|---------------------|------------------------------------|  
|**Kod błędu**|Zwrócony wynik HRESULT z wywołania.|  
|**HelpLink**|Jeśli **IErrorInfo -> HelpContext** jest różna od zera, ten ciąg jest tworzony przez łączenie **IErrorInfo -> GetHelpFile** i "#" i **IErrorInfo -> GetHelpContext**. W przeciwnym razie zostanie zwrócony ciąg z **IErrorInfo -> GetHelpFile**.|  
|**We właściwości InnerException**|Zawsze odwołanie o wartości null (**nic** w języku Visual Basic).|  
|**Komunikat**|Ciąg zwrócony przez **IErrorInfo -> GetDescription**.|  
|**Źródło**|Ciąg zwrócony przez **IErrorInfo -> GetSource**.|  
|**Ślad stosu**|Ślad stosu.|  
|**TargetSite**|Nazwa metody, która zwrócił niepowodzenie HRESULT.|  
  
 Wyjątek pól, takich jak **komunikat**, **źródła**, i **ślad stosu** nie są dostępne dla **stackoverflowexception —**.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie COM zaawansowane](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Wyjątki](../../../docs/standard/exceptions/index.md)
