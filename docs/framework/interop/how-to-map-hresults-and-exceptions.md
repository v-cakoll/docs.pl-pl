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
ms.openlocfilehash: 13dcca5f35750ad3e8bd6ea4f6dd443fe9a8ee94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123880"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Porady: mapowanie wyników HRESULT i wyjątków
Metody COM zgłaszają błędy, zwracając wartości HRESULT; metody .NET raportują je przez wyrzucanie wyjątków. Środowisko uruchomieniowe obsługuje przejście między nimi. Każda Klasa wyjątków w .NET Framework jest mapowana na wartość HRESULT.  
  
 Klasy wyjątków zdefiniowane przez użytkownika mogą określać wszelkie wartości HRESULT są odpowiednie. Te klasy wyjątków mogą dynamicznie zmieniać wynik HRESULT, który ma zostać zwrócony, gdy wyjątek jest generowany przez ustawienie pola **HRESULT** dla obiektu Exception. Dodatkowe informacje o wyjątku są udostępniane klientowi za pomocą interfejsu **IErrorInfo** , który jest implementowany w obiekcie .NET w procesie niezarządzanym.  
  
 W przypadku utworzenia klasy rozszerzającej **System. Exception**należy ustawić pole HRESULT podczas konstruowania. W przeciwnym razie Klasa bazowa przypisuje wartość HRESULT. Można mapować nowe klasy wyjątków do istniejącego HRESULT, dostarczając wartość w konstruktorze wyjątku.  
  
 Należy pamiętać, że środowisko uruchomieniowe czasami ignoruje `HRESULT` w przypadkach, gdy istnieje `IErrorInfo` w wątku.  Takie zachowanie może wystąpić w przypadkach, gdy `HRESULT` i `IErrorInfo` nie reprezentują tego samego błędu.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Aby utworzyć nową klasę wyjątku i zamapować ją na HRESULT  
  
1. Użyj poniższego kodu, aby utworzyć nową klasę wyjątku o nazwie `NoAccessException` i zamapować ją na `E_ACCESSDENIED`HRESULT.  
  
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
  
 Może wystąpić program (w dowolnym języku programowania), który jednocześnie używa kodu zarządzanego i niezarządzanego. Na przykład niestandardowy Organizator w poniższym przykładzie kodu używa metody **Marshal. ThrowExceptionForHR (int HRESULT)** , aby zgłosić wyjątek z określoną wartością HRESULT. Metoda wyszukuje wynik HRESULT i generuje odpowiedni typ wyjątku. Na przykład wynik HRESULT w poniższym fragmencie kodu generuje **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Poniższa tabela zawiera pełne mapowanie z każdego wyniku HRESULT do jego porównywalnej klasy wyjątku w .NET Framework.  
  
|HRESULT|Wyjątek platformy .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException —**|  
|**COR_E_APPLICATION**|**ApplicationException**|  
|**COR_E_ARGUMENT lub E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**Wyjątku ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC lub ERROR_ARITHMETIC_OVERFLOW**|**ArithmeticException —**|  
|**COR_E_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT lub ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**Rdzeńexception**|  
|**NTE_FAIL**|**CryptographicException**|  
|**COR_E_DIRECTORYNOTFOUND lub ERROR_PATH_NOT_FOUND**|**DirectoryNotFoundException**|  
|**COR_E_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR_E_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR_E_TYPELOAD**|**EntryPointNotFoundException —**|  
|**COR_E_EXCEPTION**|**Oprócz**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND lub ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST lub E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException —**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException —**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException —**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**IOException**|  
|**COR_E_MEMBERACCESS**|**Accessexception**|  
|**COR_E_METHODACCESS**|**MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**MissingFieldException**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR_E_MISSINGMEMBER**|**MissingMemberException**|  
|**COR_E_MISSINGMETHOD**|**MissingMethodException**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException —**|  
|**COR_E_NOTFINITENUMBER**|**NotFiniteNumberException —**|  
|**E_NOTIMPL**|**NotImplementedException**|  
|**COR_E_NOTSUPPORTED**|**NotSupportedException**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY lub**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG lub ERROR_FILENAME_EXCED_RANGE**|**PathTooLongException**|  
|**COR_E_RANK**|**RankException**|  
|**COR_E_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**RemotingException —**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException —**|  
|**COR_E_SECURITY**|**SecurityException**|  
|**COR_E_SERIALIZATION**|**SerializationException**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**StackOverflowException**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**SynchronizationLockException —**|  
|**COR_E_SYSTEM**|**SystemException**|  
|**COR_E_TARGET**|**TargetException —**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException —**|  
|**COR_E_TARGETPARAMCOUNT**|**TargetParameterCountException —**|  
|**COR_E_THREADABORTED**|**ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**ThreadInterruptedException —**|  
|**COR_E_THREADSTATE**|**ThreadStateException —**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException**|  
|**COR_E_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR_E_VERIFICATION**|**VerificationException**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Wszystkie inne HRESULT**|**COMException**|  
  
 Aby pobrać rozszerzone informacje o błędzie, zarządzany klient musi przejrzeć pola wygenerowanego obiektu wyjątku. Aby obiekt wyjątku dostarczał przydatne informacje o błędzie, obiekt COM musi implementować interfejs **IErrorInfo** . Środowisko uruchomieniowe używa informacji dostarczonych przez **IErrorInfo** do zainicjowania obiektu wyjątku.  
  
 Jeśli obiekt COM nie obsługuje **IErrorInfo**, środowisko uruchomieniowe inicjuje obiekt wyjątku z wartościami domyślnymi. Poniższa tabela zawiera listę wszystkich pól skojarzonych z obiektem wyjątku i identyfikuje źródło informacji domyślnych, gdy obiekt COM obsługuje **IErrorInfo**.  
  
 Należy pamiętać, że środowisko uruchomieniowe czasami ignoruje `HRESULT` w przypadkach, gdy istnieje `IErrorInfo` w wątku.  Takie zachowanie może wystąpić w przypadkach, gdy `HRESULT` i `IErrorInfo` nie reprezentują tego samego błędu.  
  
|Pole wyjątku|Źródło informacji z modelu COM|  
|---------------------|------------------------------------|  
|**Kodzie**|WYNIK HRESULT został zwrócony z wywołania.|  
|**HelpLink**|Jeśli **IErrorInfo-> atrybut HelpContext** jest różna od zera, ciąg jest tworzony przez złączenie **IErrorInfo-> GetHelpFile** i "#" oraz **IErrorInfo-> GetHelpContext**. W przeciwnym razie ciąg jest zwracany z **IErrorInfo-> GetHelpFile**.|  
|**InnerException**|Zawsze ma odwołanie o wartości null (**Nothing** w Visual Basic).|  
|**Komunikat**|Ciąg zwrócony z **IErrorInfo-> GetDescription**.|  
|**Zewnętrz**|Ciąg zwrócony z **IErrorInfo-> GetSource**.|  
|**Ślad stosu**|Ślad stosu.|  
|**TargetSite**|Nazwa metody, która zwróciła błąd HRESULT.|  
  
 Pola wyjątków, takie jak **Message**, **Source**i **ślad stosu** , nie są dostępne dla **StackOverflowException**.  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowana współdziałanie COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Wyjątki](../../standard/exceptions/index.md)
