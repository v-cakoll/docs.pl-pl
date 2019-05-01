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
ms.openlocfilehash: 834652318d4cb1cbcebe27a922d210ef87026ed5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872602"
---
# <a name="registering-assemblies-with-com"></a>Rejestrowanie zestawów do użycia z modelem COM
Można uruchomić z wiersza polecenia narzędzia o nazwie [narzędzie rejestracji zestawów (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) Aby zarejestrować lub wyrejestrować zestawu do użycia w modelu COM. Regasm.exe dodaje informacje o klasie do rejestru systemowego dzięki klientów modelu COM za pomocą klasy .NET Framework w sposób niewidoczny dla użytkownika. <xref:System.Runtime.InteropServices.RegistrationServices> Klasa oferuje podobne funkcje.  
  
 Zarządzany składnik musi być zarejestrowane w rejestrze systemu Windows może być aktywowany w kliencie COM. W poniższej tabeli przedstawiono klucze, które Regasm.exe dodaje się zazwyczaj do rejestru Windows. (000000 wskazuje rzeczywista wartość identyfikatora GUID).  
  
|Identyfikator GUID|Opis|Klucz rejestru|  
|----------|-----------------|------------------|  
|CLSID|Identyfikator klasy|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|Identyfikator interfejsu|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|LIBID|Identyfikator biblioteki|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|ProgID|Identyfikator programowy|HKEY_CLASSES_ROOT\000…000|  
  
 W obszarze HKCR\CLSID\\{0000... 0000} klucz, wartość domyślna jest równa ProgID klasy, a zostaną dodane dwie nowe wartości o nazwie, klasy i zestawu. Środowisko uruchomieniowe odczytuje wartość zestawu z rejestru i przekazuje je do programu rozpoznawania nazw zestawów środowiska uruchomieniowego. Mechanizm rozpoznawania zestawów próbuje zlokalizować zestawu, w oparciu o informacje o zestawie, takie jak nazwa i numer wersji. W przypadku mechanizm rozpoznawania zestawów zlokalizowania zestawu zestaw musi należeć do jednej z następujących lokalizacji:  
  
- Global assembly cache (musi być zestaw o silnej nazwie).  
  
- W katalogu aplikacji. Zestawy, ładowane z ścieżce aplikacji są dostępne jedynie z tej aplikacji.  
  
- Wzdłuż ścieżki pliku określony za pomocą **/ codebase** możliwość Regasm.exe.  
  
 Regasm.exe tworzy również klucz InProcServer32 pod HKCR\CLSID\\{0000... 0000} klucz. Wartością domyślną dla klucza jest równa nazwy biblioteki DLL, która inicjuje środowiska uruchomieniowego języka wspólnego (Mscoree.dll).  
  
## <a name="examining-registry-entries"></a>Badanie wpisów rejestru  
 Usługa międzyoperacyjna modelu COM zapewnia wdrożenie fabryki klasa standardowa w celu utworzenia wystąpienia każdej klasy .NET Framework. Klienci mogą wywołać **DllGetClassObject** na zarządzanej biblioteki DLL, aby otrzymać fabrykę klas i tworzenia obiektów, tak samo, jak za pomocą innego składnika COM.  
  
 Aby uzyskać `InprocServer32` podklucza, odwołanie do Mscoree.dll pojawia się zamiast tradycyjnych bibliotece typów modelu COM, aby wskazać, że środowiska uruchomieniowego języka wspólnego tworzy zarządzany obiekt.  
  
## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)
- [Instrukcje: Odwołanie do typów .NET z modelu COM](how-to-reference-net-types-from-com.md)
- [Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Wdrażanie aplikacji dla dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
