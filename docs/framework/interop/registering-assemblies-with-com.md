---
title: Rejestrowanie zestawów do użycia z modelem COM
description: Zarejestruj lub wyrejestruj zestawy za pomocą modelu COM za pomocą narzędzia do rejestracji zestawu (Regasm.exe), które dodaje informacje o klasie do rejestru systemowego.
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
ms.openlocfilehash: 1b73a79b8167e7f75b8c68f708179e88c575d66a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621902"
---
# <a name="registering-assemblies-with-com"></a>Rejestrowanie zestawów do użycia z modelem COM
Możesz uruchomić narzędzie wiersza polecenia o nazwie [Narzędzie rejestracji zestawu (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) , aby zarejestrować lub wyrejestrować zestaw do użycia z modelem com. Regasm.exe dodaje informacje o klasie do rejestru systemowego, aby klienci COM mogli używać klasy .NET Framework w niewidoczny sposób. <xref:System.Runtime.InteropServices.RegistrationServices>Klasa zapewnia równoważne funkcje.  
  
 Składnik zarządzany musi być zarejestrowany w rejestrze systemu Windows, aby można go było aktywować z poziomu klienta COM. W poniższej tabeli przedstawiono klucze, które Regasm.exe zwykle dodawane do rejestru systemu Windows. (000000 wskazuje rzeczywistą wartość identyfikatora GUID).  
  
|GUID|Opis|Klucz rejestru|  
|----------|-----------------|------------------|  
|Identyfikator|Identyfikator klasy|HKEY_CLASSES_ROOT \CLSID \\ {000... 500000|  
|IID|Identyfikator interfejsu|HKEY_CLASSES_ROOT \Interface \\ {000... 500000|  
|IDENTYFIKATORA LIBID|Identyfikator biblioteki|HKEY_CLASSES_ROOT \TypeLib \\ {000... 500000|  
|ProgID|Identyfikator programistyczny|HKEY_CLASSES_ROOT \ 000... 500000|  
  
 W HKCR\CLSID \\ {0000... 0000} — wartość domyślna to identyfikator ProgID klasy i dodano dwie nowe nazwane wartości, klasy i zestawu. Środowisko uruchomieniowe odczytuje wartość zestawu z rejestru i przekazuje je do programu rozpoznawania zestawu środowiska uruchomieniowego. Program rozpoznawania zestawu próbuje zlokalizować zestaw na podstawie informacji o zestawie, takich jak nazwa i numer wersji. Aby program rozpoznawania zestawu mógł zlokalizować zestaw, zestaw musi znajdować się w jednej z następujących lokalizacji:  
  
- Globalna pamięć podręczna zestawów (musi być zestawem o silnej nazwie).  
  
- katalog aplikacji. Zestawy ładowane ze ścieżki aplikacji są dostępne tylko dla tej aplikacji.  
  
- Na ścieżkę pliku określoną za pomocą opcji **/codebase** , aby Regasm.exe.  
  
 Regasm.exe również tworzy klucz InProcServer32 w HKCR\CLSID \\ {0000... 0000}. Wartość domyślna dla klucza jest ustawiana na nazwę biblioteki DLL, która inicjuje środowisko uruchomieniowe języka wspólnego (Mscoree.dll).  
  
## <a name="examining-registry-entries"></a>Badanie wpisów rejestru  
 Współdziałanie modelu COM zapewnia standardową implementację fabryki klasy w celu utworzenia wystąpienia dowolnej klasy .NET Framework. Klienci mogą wywoływać **DllGetClassObject** na ZARZĄDZANEJ bibliotece DLL, aby uzyskać fabrykę klasy i tworzyć obiekty, podobnie jak w przypadku każdego innego składnika com.  
  
 `InprocServer32`Odwołanie do Mscoree.dll pojawia się zamiast tradycyjnej biblioteki typów com, aby wskazać, że środowisko uruchomieniowe języka wspólnego tworzy obiekt zarządzany.  
  
## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)
- [Instrukcje: Odwołania do typów .NET z modelu COM](how-to-reference-net-types-from-com.md)
- [Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Wdrażanie aplikacji na potrzeby dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
