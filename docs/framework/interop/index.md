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
ms.openlocfilehash: edec95ea729fdf26e384b6658c241ca307e60851
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643117"
---
# <a name="interoperating-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym

.NET Framework wspiera interakcji z modelu COM składników modelu COM + usług, zewnętrzne biblioteki typów i wielu usług systemu operacyjnego. Typy danych, podpisy metod i mechanizmy obsługi błędów różnią się między modele obiektów zarządzanych i niezarządzanych. Aby uprościć współdziałanie składników .NET Framework, a kod niezarządzany i jej obsługi ułatwiają realizację ścieżki migracji, środowisko uruchomieniowe języka wspólnego zawiera z klientów i serwerów różnice w tych modeli obiektów.

Kod wykonujący pod kontrolą środowiska wykonawczego jest nazywany kodem zarządzanym. Z drugiej strony kod, który działa poza środowisko uruchomieniowe jest nazywany kodu niezarządzanego. Składniki COM, interfejsów ActiveX i funkcje Windows API są przykłady kodu niezarządzanego.

## <a name="in-this-section"></a>W tej sekcji

[Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)  
Opisuje sposób używania składników COM w aplikacjach .NET Framework.

[Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)  
Opisuje sposób używania składników .NET Framework z aplikacjami COM.

[Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)  
W tym artykule opisano sposób wywoływania niezarządzanego wywoływanie funkcji DLL za pomocą platformy.

[Marshaling międzyoperacyjny](interop-marshaling.md)  
W tym artykule opisano marshaling dla wywołania COM interop i platformy.

[Instrukcje: Mapa wyników HRESULT i wyjątków](how-to-map-hresults-and-exceptions.md)  
Opisuje mapowanie między wyjątków i wartości HRESULT.

[Otoki COM](com-wrappers.md)  
W tym artykule opisano otoki, dostarczone przez współdziałania z modelem COM.

[Równoważność typów i osadzone typy międzyoperacyjne](type-equivalence-and-embedded-interop-types.md)  
W tym artykule opisano, jak informacje o typie dla typów modelu COM jest osadzony w zestawach i jak środowisko uruchomieniowe języka wspólnego określa równoważności typów modelu COM, embedded.

[Instrukcje: Generowanie zestawów podstawowej obsługi Międzyoperacyjnej przy użyciu Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Opisuje sposób tworzenia podstawowych zestawów międzyoperacyjnych, za pomocą *Tlbimp.exe* (Importer biblioteki typów).

[Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych](how-to-register-primary-interop-assemblies.md)  
W tym artykule opisano, jak zarejestrować podstawowe zestawy międzyoperacyjne, zanim można się odwołać je w swoich projektach.

[Współdziałanie z COM bez rejestrowania](registration-free-com-interop.md)  
W tym artykule opisano, jak Usługa międzyoperacyjna modelu COM może zostać aktywowany składniki bez za pomocą rejestru Windows.

[Instrukcje: Konfigurowanie składników COM opartych na Framework .NET aktywacji bez rejestracji](configure-net-framework-based-com-components-for-reg.md)  
W tym artykule opisano sposób tworzenia manifestu aplikacji oraz jak utworzyć i osadzanie manifestu składnika.
