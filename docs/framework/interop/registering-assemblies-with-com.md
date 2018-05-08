---
title: Rejestrowanie zestawów do użycia z modelem COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92f36488dec113dcffffac3e6cdc0c26a690b5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="registering-assemblies-with-com"></a>Rejestrowanie zestawów do użycia z modelem COM
Można uruchomić narzędzie wiersza polecenia o nazwie [narzędzie rejestracji zestawów (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) do zarejestrowania lub wyrejestrowania zestawu do użytku z modelu COM. Regasm.exe dodaje informacje o klasie w rejestrze systemu, więc klientów modelu COM można użyć klasy .NET Framework w sposób niewidoczny dla użytkownika. <xref:System.Runtime.InteropServices.RegistrationServices> Klasa udostępnia podobne funkcje.  
  
 Zanim można aktywować z klient modelu COM, w rejestrze systemu Windows należy zarejestrować zarządzanego składnika. W poniższej tabeli przedstawiono kluczy, które Regasm.exe zazwyczaj dodaje do rejestru systemu Windows. (000000 wskazuje rzeczywistą wartość identyfikatora GUID).  
  
|Identyfikator GUID|Opis|Klucz rejestru|  
|----------|-----------------|------------------|  
|CLSID|Identyfikator klasy|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|Identyfikator interfejsu|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|LIBID|Identyfikator biblioteki|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|Identyfikator programu|Identyfikator programowy|HKEY_CLASSES_ROOT\000…000|  
  
 W obszarze HKCR\CLSID\\{0000... 0000} klucza, wartość domyślna jest równa ProgID klasy i zostaną dodane dwa nowe nazwanych wartości, klasy i zestawu. Środowisko uruchomieniowe odczytuje wartość zestawu z rejestru i przekazywane do rozpoznawania zestawu środowiska wykonawczego. Mechanizm rozpoznawania zestawów próbuje zlokalizować zestawu, na podstawie zestawu informacji takich jak nazwa i numer wersji. Dla rozpoznawania zestawu do zlokalizowania zestawu zestawu musi być w jednym z następujących lokalizacji:  
  
-   Globalna pamięć podręczna zestawów (musi być to zestaw o silnej nazwie).  
  
-   W katalogu aplikacji. Zestawów załadowanych w ścieżce aplikacji są dostępne jedynie z tej aplikacji.  
  
-   Wzdłuż ścieżki pliku określony za pomocą **/ codebase** możliwość Regasm.exe.  
  
 Regasm.exe tworzy także klucz InProcServer32 w HKCR\CLSID\\{0000... 0000} klucz. Wartość domyślna dla klucza ma ustawioną nazwę biblioteki dll, która inicjuje środowisko uruchomieniowe języka wspólnego (Mscoree.dll).  
  
## <a name="examining-registry-entries"></a>Badanie wpisów rejestru  
 Współdziałanie z COM udostępnia implementację fabryki klasy standardowych można utworzyć wystąpienia każdej klasy .NET Framework. Klienci mogą wywoływać **metody DllGetClassObject** na zarządzanej biblioteki DLL, aby otrzymać fabrykę klas i tworzenie obiektów, podobnie jak inne składnika COM.  
  
 Aby uzyskać `InprocServer32` podklucza, zamiast tradycyjnych Biblioteka typów COM, aby wskazać, że środowisko uruchomieniowe języka wspólnego tworzy obiekt zarządzany pojawi się odwołanie do biblioteki Mscoree.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)  
 [Instrukcje: Odwołania do typów .NET z modelu COM](how-to-reference-net-types-from-com.md)  
 [Wywołanie obiektu .NET.](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))  
 [Wdrażanie aplikacji na potrzeby dostępu modelu COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))
