---
title: Współdziałanie z kodem niezarządzanym
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 583cfb6e3a5145c6c0dfc82ec9ff64c6d87414ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interoperating-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym

.NET Framework zamienia interakcji z COM składników, COM + usług, bibliotek typu zewnętrznego i wiele usług systemu operacyjnego. Typy danych, podpisy metod i mechanizmy obsługi błędów różnić modele obiektów zarządzanych i niezarządzanych. Aby uprościć współdziałanie między składników .NET Framework i kodu niezarządzanego i ścieżki migracji do jej obsługi ułatwiają, środowisko uruchomieniowe języka wspólnego zawiera od klientów i serwerów różnice w tych modeli obiektów.

Kod, który wykonuje pod kontrolą środowiska uruchomieniowego jest wywoływana kodu zarządzanego. Z drugiej strony kod uruchamiany poza środowisko wykonawcze jest nazywany kodu niezarządzanego. Składniki modelu COM, interfejsy ActiveX i funkcji Win32 API są przykłady kodu niezarządzanego.

## <a name="in-this-section"></a>W tej sekcji

[Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)  
Informacje dotyczące używania składniki COM w aplikacjach .NET Framework.

[Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)  
Informacje dotyczące używania składników .NET Framework z aplikacjami COM.

[Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)  
Opisuje sposób wywoływania niezarządzanego wywołanie funkcji DLL przy użyciu platformy.

[Marshaling międzyoperacyjny](interop-marshaling.md)  
Opisuje, przekazywanie do wywoływania platformy i COM interop.

[Instrukcje: Mapowanie wyników HRESULT i wyjątków](how-to-map-hresults-and-exceptions.md)  
Opisuje mapowanie między wyjątki i wyników HRESULT.

[Otoki COM](com-wrappers.md)  
W tym artykule opisano otoki podał COM interop.

[Równoważność typów i osadzone typy międzyoperacyjne](type-equivalence-and-embedded-interop-types.md)  
Opisuje sposób informacje o typie dla typów COM jest osadzony w zestawach i jak środowisko uruchomieniowe języka wspólnego określa równoważność osadzone typy COM.

[Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Opisuje sposób tworzenia podstawowe zestawy międzyoperacyjne przy użyciu *Tlbimp.exe* (Importer biblioteki typów).

[Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych](how-to-register-primary-interop-assemblies.md)  
Opisuje sposób rejestrowania podstawowe zestawy międzyoperacyjne, zanim można odwoływać się je w projektach.

[Współdziałanie z COM bez rejestrowania](registration-free-com-interop.md)  
W tym artykule opisano, jak Usługa międzyoperacyjna modelu COM może aktywować składniki bez za pomocą rejestru systemu Windows.

[Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework](configure-net-framework-based-com-components-for-reg.md)  
Opisuje sposób tworzenia manifest aplikacji oraz tworzenie i osadzanie manifestu składnika.
