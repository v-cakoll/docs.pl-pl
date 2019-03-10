---
title: Konfigurowanie walidacji działania
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 65928de1dc8b8d9914648463a136790c7978f53c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704560"
---
# <a name="configuring-activity-validation"></a>Konfigurowanie walidacji działania
Działanie sprawdzania poprawności umożliwia działanie autorzy i użytkowników zidentyfikować i raportowania błędów w konfiguracji działanie przed jej wykonanie. Windows Workflow Foundation (WF) udostępnia następujące trzy typy walidacji działania:  
  
-   `RequiredArgument` i `OverloadGroup` atrybutów.  
  
-   Imperatywne sprawdzanie poprawności opartego na kodzie.  
  
-   Ograniczenia deklaratywne.  
  
 `RequiredArgument` i `OverloadGroup` atrybuty wskazać, że niektóre argumenty w ramach działania są wymagane. Imperatywne sprawdzanie poprawności, które są oparte na kodzie zapewnia prostą metodę dla działania w celu udostępnienia weryfikacji o sobie i ograniczenia deklaratywne włączyć weryfikację o aktywności i jej relacji z zawierającego przepływu pracy. Jeśli działanie nie jest prawidłowo skonfigurowany zgodnie z wymaganiami sprawdzania poprawności, zwracane są błędy i ostrzeżenia walidacji. Jeśli zawierającego przepływu pracy zostało utworzone za pomocą projektanta przepływów pracy, wszelkie błędy sprawdzania poprawności i ostrzeżenia są wyświetlane w projektancie. Jeśli przepływ pracy został utworzony poza projektanta przepływów pracy wszelkie błędy sprawdzania poprawności są zwracane, gdy przepływ pracy zostanie wywołany. Niezależnie od tego, jak przepływ pracy został utworzony przepływ pracy o błędy sprawdzania poprawności nigdy nie może być wykonywane. Ta sekcja zawiera omówienie tego rodzaju sprawdzania poprawności działania i jak działanie sprawdzania poprawności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wymagane argumenty i grupy metod przeciążonych](required-arguments-and-overload-groups.md)  
 Opisuje sposób używania `RequiredArgument` i `OverloadGroup` atrybutów w celu udostępnienia weryfikacji.  
  
 [Walidacja oparta na kodzie imperatywnym](imperative-code-based-validation.md)  
 Opisuje sposób używania weryfikacji oparte na kodzie <xref:System.Activities.CodeActivity> i <xref:System.Activities.NativeActivity> na podstawie działania.  
  
 [Ograniczenia deklaratywne](declarative-constraints.md)  
 Opisuje sposób używania ograniczenia deklaratywne w celu udostępnienia weryfikacji złożone działania.  
  
 [Wywoływanie walidacji działania](invoking-activity-validation.md)  
 W tym artykule omówiono podczas walidacji działania jest wywoływane automatycznie oraz sposób jawnego wywołania sprawdzania poprawności.  
  
## <a name="reference"></a>Tematy pomocy  
  
## <a name="related-sections"></a>Sekcje pokrewne
