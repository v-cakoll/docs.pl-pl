---
title: Współdziałanie z kodem niezarządzanym
description: Przegląd międzyoperacyjności z niezarządzanym kodem. Środowisko CLR jest ukryte od klientów i serwerów, w których modele obiektów składników .NET i niezarządzanego kodu różnią się.
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
ms.openlocfilehash: 1cebd75907fd202715cb337593186d248107bdbb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621876"
---
# <a name="interoperating-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym

.NET Framework promuje interakcje ze składnikami COM, usługami COM+, bibliotekami typów zewnętrznych i wieloma usługami systemu operacyjnego. Typy danych, sygnatury metod i mechanizmy obsługi błędów różnią się między zarządzanymi i niezarządzanymi modelami obiektów. Aby uprościć współdziałanie między składnikami .NET Framework i niezarządzanym kodem, a w celu ułatwienia ścieżki migracji, środowisko uruchomieniowe języka wspólnego jest ukrywane zarówno w przypadku klientów, jak i serwerów, które różnią się w tych modelach obiektów.

Kod wykonywany w ramach kontroli środowiska uruchomieniowego jest nazywany kodem zarządzanym. Z kolei kod, który działa poza środowiskiem uruchomieniowym, jest nazywany kodem niezarządzanym. Składniki COM, interfejsy ActiveX i funkcje interfejsu API systemu Windows to przykłady kodu niezarządzanego.

## <a name="in-this-section"></a>W tej sekcji

[Udostępnianie składników COM programowi.NET Framework](exposing-com-components.md)  
Opisuje, jak używać składników COM z aplikacji .NET Framework.

[Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)  
Opisuje, jak używać składników .NET Framework z aplikacji COM.

[Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)  
Opisuje sposób wywoływania niezarządzanych funkcji DLL przy użyciu wywołania platformy.

[Organizowanie międzyoperacyjne](interop-marshaling.md)  
Opisuje kierowanie dla międzyoperacyjności modelu COM i wywołania platformy.

[Instrukcje: Mapowanie wyników HRESULT i wyjątków](how-to-map-hresults-and-exceptions.md)  
Opisuje mapowanie między wyjątkami i WYNIKami HRESULT.

[Równoważność typów i osadzone typy międzyoperacyjne](type-equivalence-and-embedded-interop-types.md)  
Opisuje, jak informacje o typie dla typów COM są osadzone w zestawach oraz jak środowisko uruchomieniowe języka wspólnego określa równoważność osadzonych typów COM.

[Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Opisuje sposób tworzenia podstawowych zestawów międzyoperacyjnych przy użyciu *Tlbimp.exe* (Importer biblioteki typów).

[Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych](how-to-register-primary-interop-assemblies.md)  
W tym artykule opisano sposób rejestrowania podstawowych zestawów międzyoperacyjnych, zanim będzie można odwołać się do nich w projektach.

[Współdziałanie z modelem COM bez rejestrowania](registration-free-com-interop.md)  
Opisuje sposób, w jaki współdziałanie modelu COM może aktywować składniki bez używania rejestru systemu Windows.

[Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework](configure-net-framework-based-com-components-for-reg.md)  
Opisuje sposób tworzenia manifestu aplikacji i tworzenia i osadzania manifestu składnika.

## <a name="related-sections"></a>Sekcje pokrewne

[Otoki COM](../../standard/native-interop/com-wrappers.md)  
Opisuje otoki udostępniane przez międzyoperacyjność modelu COM.
