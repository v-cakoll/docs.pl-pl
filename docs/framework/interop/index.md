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
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457971"
---
# <a name="interoperating-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym

Program .NET Framework promuje interakcję ze składnikami COM, usługami COM+, bibliotekami typów zewnętrznych i wieloma usługami systemu operacyjnego. Typy danych, podpisy metod i mechanizmy obsługi błędów różnią się w zależności od modeli obiektów zarządzanych i niezarządzanych. Aby uprościć współdziałanie między składnikami programu .NET Framework i kodem niezarządzanym i ułatwić ścieżkę migracji, środowisko wykonawcze języka wspólnego ukrywa przed klientami i serwerami różnice w tych modelach obiektów.

Kod, który wykonuje pod kontrolą środowiska wykonawczego jest nazywany kodem zarządzanym. Z drugiej strony kod, który działa poza środowisko wykonawcze jest nazywany kodem niezarządzanym. Składniki COM, interfejsy ActiveX i funkcje interfejsu API systemu Windows są przykładami niezarządzanego kodu.

## <a name="in-this-section"></a>W tej sekcji

[Udostępnianie składników COM programowi.NET Framework](exposing-com-components.md)  
W tym artykule opisano sposób używania składników COM z aplikacji .NET Framework.

[Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)  
W tym artykule opisano sposób używania składników .NET Framework z aplikacji COM.

[Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)  
W tym artykule opisano sposób wywoływania niezarządzanych funkcji DLL przy użyciu platformy wywołać.

[Organizowanie międzyoperacyjne](interop-marshaling.md)  
Opisuje kierowanie dla com interop i platformy wywołać.

[Porady: mapowanie wyników HRESULT i wyjątków](how-to-map-hresults-and-exceptions.md)  
Opisuje mapowanie między wyjątkami i HRESULTs.

[Równoważność typów i osadzone typy międzyoperacyjne](type-equivalence-and-embedded-interop-types.md)  
W tym artykule opisano, jak informacje o typie dla typów COM są osadzane w zestawach i jak środowisko uruchomieniowe języka wspólnego określa równoważność osadzonych typów COM.

[Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
W tym artykule opisano sposób tworzenia podstawowych zestawów międzyoperacyjnych przy użyciu *programu Tlbimp.exe* (importer biblioteki typów).

[Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych](how-to-register-primary-interop-assemblies.md)  
W tym artykule opisano sposób rejestrowania podstawowych zestawów międzyoperacyjnych, zanim będzie można odwoływać się do nich w projektach.

[Współdziałanie z COM bez rejestrowania](registration-free-com-interop.md)  
W tym artykule opisano, jak com interop można aktywować składniki bez korzystania z rejestru systemu Windows.

[Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework](configure-net-framework-based-com-components-for-reg.md)  
W tym artykule opisano sposób tworzenia manifestu aplikacji oraz sposobu tworzenia i osadzania manifestu składnika.

## <a name="related-sections"></a>Powiązane sekcje

[Otoki COM](../../standard/native-interop/com-wrappers.md)  
Opisuje otoki dostarczone przez współdziałanie COM.
