---
title: 'Instrukcje: Mapowanie wyników HRESULT i wyjątków'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60173739842835a705a72da4e7ab442cacfc08d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643052"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Instrukcje: Mapowanie wyników HRESULT i wyjątków
Metody modelu COM, raportowanie błędów przez zwrócenie wartości HRESULT; metod .NET zgłoszenie ich przez zgłaszanie wyjątków. Środowisko wykonawcze obsługuje przejścia między nimi. Każda klasa wyjątków w programie .NET Framework jest mapowany na HRESULT.  
  
 Klasy wyjątków zdefiniowanych przez użytkownika można określić, niezależnie od rodzaju HRESULT jest odpowiednia. Te klasy wyjątku można dynamicznie zmieniać HRESULT zwracane, gdy wyjątek jest generowany przez ustawienie **HResult** pola obiektu wyjątku. Dodatkowe informacje o wyjątku jest udostępniany za pośrednictwem **IErrorInfo** interfejs, który jest zaimplementowany dla obiektu .NET w proces niezarządzany.  
  
 Jeśli tworzysz klasę, która rozszerza **System.Exception**, należy ustawić pola HRESULT podczas konstruowania. W przeciwnym razie klasa bazowa przypisuje wartość HRESULT. Nowe klasy wyjątku można zamapować na istniejące HRESULT, poprzez dostarczenie wartości w Konstruktorze wyjątku.  
  
 Należy zauważyć, że czasami zignoruje środowiska uruchomieniowego `HRESULT` w przypadkach, w przypadku, gdy istnieje `IErrorInfo` obecne w wątku.  To zachowanie może występować w przypadku których `HRESULT` i `IErrorInfo` nie reprezentują ten sam błąd.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Tworzenie nowej klasy wyjątku i Mapuj na HRESULT  
  
1. Użyj poniższego kodu, aby utworzyć nową klasę wyjątków, o nazwie `NoAccessException` i mapowanie ich na HRESULT `E_ACCESSDENIED`.  
  
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
  
 Może wystąpić programu (w dowolnym języku programowania), który używa kodu zarządzanych i niezarządzanych, w tym samym czasie. Na przykład organizatora niestandardowego w poniższym przykładzie kodu użyto **Marshal.ThrowExceptionForHR (int HResult)** metodę, aby zgłosić wyjątek z określoną wartością HRESULT. Metoda wyszukuje HRESULT i generuje typ odpowiedni wyjątek. Na przykład generuje wartości HRESULT w następujący fragment kodu **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Poniższa tabela zawiera pełną mapowanie od każdego HRESULT do jej klasy porównywalne wyjątek w .NET Framework.  
  
|HRESULT|Wyjątek dla platformy .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR_E_APPLICATION**|**Applicationexception —**|  
|**COR_E_ARGUMENT lub E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**Trwa wyjątku ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC lub ERROR_ARITHMETIC_OVERFLOW**|**Arithmeticexception —**|  
|**COR_E_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT lub ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**CryptographicException**|  
|**COR_E_DIRECTORYNOTFOUND lub ERROR_PATH_NOT_FOUND**|**DirectoryNotFoundException**|  
|**COR_E_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR_E_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR_E_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR_E_EXCEPTION**|**wyjątek**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND lub ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST lub E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**IOException**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**MissingFieldException**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR_E_MISSINGMEMBER**|**MissingMemberException**|  
|**COR_E_MISSINGMETHOD**|**MissingMethodException**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException**|  
|**COR_E_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E_NOTIMPL**|**NotImplementedException**|  
|**COR_E_NOTSUPPORTED**|**NotSupportedException**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY lub**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG lub ERROR_FILENAME_EXCED_RANGE**|**PathTooLongException**|  
|**COR_E_RANK**|**RankException**|  
|**COR_E_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**Remotingexception —**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException**|  
|**COR_E_SECURITY**|**SecurityException**|  
|**COR_E_SERIALIZATION**|**SerializationException**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**StackOverflowException**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**Synchronizationlockexception —**|  
|**COR_E_SYSTEM**|**SystemException**|  
|**COR_E_TARGET**|**TargetException**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**TargetParameterCountException**|  
|**COR_E_THREADABORTED**|**ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR_E_THREADSTATE**|**ThreadStateException**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException**|  
|**COR_E_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR_E_VERIFICATION**|**Verificationexception —**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Wszystkie inne wartości HRESULT**|**COMException**|  
  
 Aby uzyskać rozszerzone informacje o błędzie, zarządzanego klienta należy zbadać pola obiektu wyjątku, który został wygenerowany. Obiekt wyjątku dostarczyć przydatnych informacji o błędzie, musisz zaimplementować obiekt COM **IErrorInfo** interfejsu. Środowisko wykonawcze używa informacji dostarczonych przez **IErrorInfo** można zainicjować obiektu wyjątku.  
  
 Jeśli obiekt COM nie obsługuje **IErrorInfo**, środowisko uruchomieniowe inicjuje obiekt wyjątku z wartościami domyślnymi. Poniższa tabela zawiera listę pól, skojarzony obiekt wyjątku i zidentyfikować źródło domyślne informacje, kiedy obiekt COM obsługuje **IErrorInfo**.  
  
 Należy zauważyć, że czasami zignoruje środowiska uruchomieniowego `HRESULT` w przypadkach, w przypadku, gdy istnieje `IErrorInfo` obecne w wątku.  To zachowanie może występować w przypadku których `HRESULT` i `IErrorInfo` nie reprezentują ten sam błąd.  
  
|Pole wyjątku|Źródło informacji z modelu COM|  
|---------------------|------------------------------------|  
|**ErrorCode**|HRESULT zwracane z wywołania.|  
|**HelpLink**|Jeśli **IErrorInfo -> helpcontext —** jest różna od zera, ciąg jest tworzona przez złączenie **IErrorInfo -> GetHelpFile** i "#" i **IErrorInfo -> GetHelpContext**. W przeciwnym razie zostanie zwrócony ciąg z **IErrorInfo -> GetHelpFile**.|  
|**Wyjątek wewnętrzny**|Zawsze odwołanie o wartości null (**nic** w języku Visual Basic).|  
|**Komunikat**|Ciąg zwracany z **IErrorInfo -> GetDescription**.|  
|**Element źródłowy**|Ciąg zwracany z **IErrorInfo -> GetSource**.|  
|**StackTrace**|Ślad stosu.|  
|**TargetSite**|Nazwa metody, która jest zwracana niepowodzenia HRESULT.|  
  
 Wyjątek pola, takie jak **komunikat**, **źródła**, i **ślad stosu** nie są dostępne dla **stackoverflowexception —**.  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane współdziałanie modeli COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Wyjątki](../../standard/exceptions/index.md)
