---
title: Rejestrowanie zestawów do użycia z modelem COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
ms.openlocfilehash: 9ff24a5705058d4e303b3b64b454ced8548053a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113807"
---
# <a name="registering-assemblies-with-com"></a>Rejestrowanie zestawów do użycia z modelem COM
Możesz uruchomić narzędzie wiersza polecenia o nazwie [Narzędzie rejestracji zestawu (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) , aby zarejestrować lub wyrejestrować zestaw do użycia z modelem com. Regasm. exe dodaje informacje o klasie do rejestru systemowego, aby klienci COM mogli używać klasy .NET Framework w niewidoczny sposób. <xref:System.Runtime.InteropServices.RegistrationServices> Klasa zapewnia równoważne funkcje.  
  
 Składnik zarządzany musi być zarejestrowany w rejestrze systemu Windows, aby można go było aktywować z poziomu klienta COM. W poniższej tabeli przedstawiono klucze, które Regasm. exe są zazwyczaj dodawane do rejestru systemu Windows. (000000 wskazuje rzeczywistą wartość identyfikatora GUID).  
  
|Identyfikator GUID|Opis|Klucz rejestru|  
|----------|-----------------|------------------|  
|Identyfikator|Identyfikator klasy|HKEY_CLASSES_ROOT \CLSID\\{000... 500000|  
|IID|Identyfikator interfejsu|HKEY_CLASSES_ROOT \Interface\\{000... 500000|  
|IDENTYFIKATORA LIBID|Identyfikator biblioteki|HKEY_CLASSES_ROOT \TypeLib\\{000... 500000|  
|ProgID|Identyfikator programistyczny|HKEY_CLASSES_ROOT \ 000... 500000|  
  
 W HKCR\CLSID\\{0000... 0000} — wartość domyślna to identyfikator ProgID klasy i dodano dwie nowe nazwane wartości, klasy i zestawu. Środowisko uruchomieniowe odczytuje wartość zestawu z rejestru i przekazuje je do programu rozpoznawania zestawu środowiska uruchomieniowego. Program rozpoznawania zestawu próbuje zlokalizować zestaw na podstawie informacji o zestawie, takich jak nazwa i numer wersji. Aby program rozpoznawania zestawu mógł zlokalizować zestaw, zestaw musi znajdować się w jednej z następujących lokalizacji:  
  
- Globalna pamięć podręczna zestawów (musi być zestawem o silnej nazwie).  
  
- katalog aplikacji. Zestawy ładowane ze ścieżki aplikacji są dostępne tylko dla tej aplikacji.  
  
- Ścieżka pliku określona z opcją **/codebase** do Regasm. exe.  
  
 Regasm. exe tworzy również klucz InProcServer32 w HKCR\CLSID\\{0000... 0000}. Wartość domyślna dla klucza jest ustawiana na nazwę biblioteki DLL, która inicjuje środowisko uruchomieniowe języka wspólnego (mscoree. dll).  
  
## <a name="examining-registry-entries"></a>Badanie wpisów rejestru  
 Współdziałanie modelu COM zapewnia standardową implementację fabryki klasy w celu utworzenia wystąpienia dowolnej klasy .NET Framework. Klienci mogą wywoływać **DllGetClassObject** na ZARZĄDZANEJ bibliotece DLL, aby uzyskać fabrykę klasy i tworzyć obiekty, podobnie jak w przypadku każdego innego składnika com.  
  
 W przypadku `InprocServer32` podklucza, odwołanie do biblioteki Mscoree. dll występuje zamiast tradycyjnego modelu COM, aby wskazać, że środowisko uruchomieniowe języka wspólnego tworzy obiekt zarządzany.  
  
## <a name="see-also"></a>Zobacz też

- [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)
- [Instrukcje: Odwołania do typów .NET z modelu COM](how-to-reference-net-types-from-com.md)
- [Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Wdrażanie aplikacji na potrzeby dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
