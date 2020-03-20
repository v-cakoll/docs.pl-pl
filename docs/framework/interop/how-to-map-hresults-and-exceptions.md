---
title: 'Porady: mapowanie wyników HRESULT i wyjątków'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
ms.openlocfilehash: e186228d1dc9a42ddfe92428f7dfad29a5789095
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181404"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Porady: mapowanie wyników HRESULT i wyjątków
Metody COM zgłaszają błędy, zwracając hresulty; metody .NET zgłaszają je, zgłaszając wyjątki. Środowisko wykonawcze obsługuje przejście między tymi dwoma. Każda klasa wyjątku w .NET Framework mapuje do HRESULT.  
  
 Klasy wyjątków zdefiniowane przez użytkownika można określić, co HRESULT jest odpowiedni. Te klasy wyjątków można dynamicznie zmienić HRESULT do zwrotu, gdy wyjątek jest generowany przez ustawienie **HResult** pole na obiekt wyjątku. Dodatkowe informacje o wyjątku są dostarczane do klienta za pośrednictwem interfejsu **IErrorInfo,** który jest implementowany w obiekcie .NET w procesie niezarządzanym.  
  
 W przypadku utworzenia klasy rozszerza jące **system.exception**należy ustawić pole HRESULT podczas budowy. W przeciwnym razie klasa podstawowa przypisuje wartość HRESULT. Można mapować nowe klasy wyjątków do istniejącego HRESULT, podając wartość w konstruktorze wyjątku.  
  
 Należy zauważyć, że środowisko `HRESULT` wykonawcze czasami ignoruje w przypadkach, gdy istnieje `IErrorInfo` obecny w wątku.  To zachowanie może wystąpić `HRESULT` w `IErrorInfo` przypadkach, gdy i nie reprezentują tego samego błędu.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Aby utworzyć nową klasę wyjątku i zamapować ją na hresult  
  
1. Użyj następującego kodu, aby utworzyć `NoAccessException` nową klasę wyjątku `E_ACCESSDENIED`o nazwie i zamapować go na HRESULT .  
  
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
  
 Może wystąpić program (w dowolnym języku programowania), który używa zarówno kodu zarządzanego, jak i niezarządzanego w tym samym czasie. Na przykład niestandardowy organizator w poniższym przykładzie kodu używa **metody Marshal.ThrowExceptionForHR(int HResult),** aby zgłosić wyjątek o określonej wartości HRESULT. Metoda wyszukuje HRESULT i generuje odpowiedni typ wyjątku. Na przykład HRESULT w poniższym fragmencie kodu generuje **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Poniższa tabela zawiera pełne mapowanie z każdego HRESULT do porównywalnej klasy wyjątków w .NET Framework.  
  
|HRESULT|Wyjątek .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**Appdomainunloadedexception**|  
|**COR_E_APPLICATION**|**Applicationexception**|  
|**COR_E_ARGUMENT lub E_INVALIDARG**|**Zeksuw argumentów**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**Kreślenie argumentów**|  
|**COR_E_ARITHMETIC lub ERROR_ARITHMETIC_OVERFLOW**|**Arithmeticexception**|  
|**COR_E_ARRAYTYPEMISMATCH**|**Arraytypemismatchexception**|  
|**COR_E_BADIMAGEFORMAT lub ERROR_BAD_FORMAT**|**Badimageformatexception**|  
|**COR_E_COMEMULATE_ERROR**|**ComEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**Contextmarshalexception**|  
|**COR_E_CORE**|**CoreException (Nieekceptiona)**|  
|**NTE_FAIL**|**Cryptographicexception**|  
|**COR_E_DIRECTORYNOTFOUND lub ERROR_PATH_NOT_FOUND**|**Directorynotfoundexception**|  
|**COR_E_DIVIDEBYZERO**|**Dividebyzeroexception**|  
|**COR_E_DUPLICATEWAITOBJECT**|**Duplicatewaitobjectexception**|  
|**COR_E_ENDOFSTREAM**|**Endofstreamexception**|  
|**COR_E_TYPELOAD**|**Entrypointnotfoundexception**|  
|**Cor_e_exception**|**Wyjątek**|  
|**COR_E_EXECUTIONENGINE**|**Executionengineexception**|  
|**COR_E_FIELDACCESS**|**Fieldaccessexception**|  
|**COR_E_FILENOTFOUND lub ERROR_FILE_NOT_FOUND**|**Filenotfoundexception**|  
|**COR_E_FORMAT**|**Formatexception**|  
|**COR_E_INDEXOUTOFRANGE**|**Indexoutofrangeexception**|  
|**COR_E_INVALIDCAST lub E_NOINTERFACE**|**InwersjaException**|  
|**COR_E_INVALIDCOMOBJECT**|**Invalidcomobjectexception**|  
|**COR_E_INVALIDFILTERCRITERIA**|**Invalidfiltercriteriaexception**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**Invalidolevarianttypeexception**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**Ioexception**|  
|**COR_E_MEMBERACCESS**|**DostępException**|  
|**COR_E_METHODACCESS**|**Methodaccessexception**|  
|**COR_E_MISSINGFIELD**|**Missingfieldexception**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**Missingmanifestresourceexception**|  
|**COR_E_MISSINGMEMBER**|**Missingmemberexception**|  
|**COR_E_MISSINGMETHOD**|**Missingmethodexception**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**Multicastnotsupportedexception**|  
|**COR_E_NOTFINITENUMBER**|**Notfinitenumberexception**|  
|**E_notimpl**|**Notimplementedexception**|  
|**COR_E_NOTSUPPORTED**|**Notsupportedexception**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**Nullreferenceexception**|  
|**COR_E_OUTOFMEMORY lub**<br /><br /> **E_outofmemory**|**Outofmemoryexception**|  
|**COR_E_OVERFLOW**|**Nadmiernezamykanie**|  
|**COR_E_PATHTOOLONG lub ERROR_FILENAME_EXCED_RANGE**|**Pathtoolongexception**|  
|**COR_E_RANK**|**Rankexception**|  
|**COR_E_REFLECTIONTYPELOAD**|**Reflectiontypeloadexception**|  
|**COR_E_REMOTING**|**Remotingexception**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**Safearraytypemismatchexception**|  
|**COR_E_SECURITY**|**Securityexception**|  
|**COR_E_SERIALIZATION**|**Serializationexception**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**Stackoverflowexception**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**Synchronizationlockexception**|  
|**COR_E_SYSTEM**|**Systemexception**|  
|**COR_E_TARGET**|**Targetexception**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**Targetparametercountexception**|  
|**COR_E_THREADABORTED**|**Threadabortexception**|  
|**COR_E_THREADINTERRUPTED**|**Threadinterruptedexception**|  
|**COR_E_THREADSTATE**|**Threadstateexception**|  
|**COR_E_THREADSTOP**|**ThreadStopException (Nieekception)**|  
|**COR_E_TYPELOAD**|**Typeloadexception**|  
|**COR_E_TYPEINITIALIZATION**|**Typeinitializationexception**|  
|**COR_E_VERIFICATION**|**Verificationexception**|  
|**COR_E_WEAKREFERENCE**|**Słabewystawianie odwołań**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Wszystkie inne hresults**|**Comexception**|  
  
 Aby pobrać informacje o błąd rozszerzony, klient zarządzany musi zbadać pola obiektu wyjątku, który został wygenerowany. Aby obiekt wyjątku dostarczył przydatnych informacji o błędzie, obiekt COM musi implementować interfejs **IErrorInfo.** Środowisko wykonawcze używa informacji dostarczonych przez **IErrorInfo** do zainicjowania obiektu wyjątku.  
  
 Jeśli obiekt COM nie obsługuje **iErrorInfo,** środowisko wykonawcze inicjuje obiekt wyjątku z wartościami domyślnymi. W poniższej tabeli wymieniono każde pole skojarzone z obiektem wyjątku i identyfikuje źródło informacji domyślnych, gdy obiekt COM obsługuje **program IErrorInfo**.  
  
 Należy zauważyć, że środowisko `HRESULT` wykonawcze czasami ignoruje w przypadkach, gdy istnieje `IErrorInfo` obecny w wątku.  To zachowanie może wystąpić `HRESULT` w `IErrorInfo` przypadkach, gdy i nie reprezentują tego samego błędu.  
  
|Pole wyjątku|Źródło informacji od COM|  
|---------------------|------------------------------------|  
|**Errorcode**|HRESULT powrócił z połączenia.|  
|**Helplink**|Jeśli **IErrorInfo->HelpContext** jest niezerowy, ciąg jest tworzony przez łączenie **IErrorInfo->GetHelpFile** i "#" i **IErrorInfo->GetHelpContext**. W przeciwnym razie ciąg jest zwracany z **IErrorInfo->GetHelpFile**.|  
|**Innerexception**|Zawsze odwołanie null (**Nic** w języku Visual Basic).|  
|**Komunikat**|Ciąg zwrócony z **IErrorInfo->GetDescription**.|  
|**Źródła**|Ciąg zwrócony z **IErrorInfo->GetSource**.|  
|**Stacktrace**|Ślad stosu.|  
|**Targetsite**|Nazwa metody, która zwróciła niepowodzenie HRESULT.|  
  
 Pola wyjątków, takie jak **Message**, **Source**i **StackTrace,** nie są dostępne dla **stackoverflowException**.  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowana interoperacyjność COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Wyjątki](../../standard/exceptions/index.md)
