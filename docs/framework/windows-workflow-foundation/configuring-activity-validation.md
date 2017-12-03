---
title: "Konfigurowanie sprawdzania poprawności działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 440f3ee85fe24707c6bb433736bf6104d9e0dfc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-activity-validation"></a>Konfigurowanie sprawdzania poprawności działania
Działanie sprawdzania poprawności umożliwia autorów działania i użytkowników zidentyfikować i raportów o błędach w konfiguracji działania przed jego wykonywania. [!INCLUDE[wf](../../../includes/wf-md.md)]udostępnia następujące trzy typy sprawdzania poprawności działania:  
  
-   `RequiredArgument`i `OverloadGroup` atrybutów.  
  
-   Konieczne weryfikacji opartych na kodzie.  
  
-   Deklaracyjne ograniczenia.  
  
 `RequiredArgument`i `OverloadGroup` atrybuty wskazać, że niektóre argumenty w działaniu są wymagane. Konieczne weryfikacji opartych na kodzie zapewnia prosty sposób działania w celu udostępnienia weryfikacji o sobie, a ograniczenia deklaratywne włączyć weryfikację o aktywności i ich relacji z zawierającego przepływu pracy. Jeśli działanie nie jest prawidłowo skonfigurowany zgodnie z wymaganiami weryfikacji, zwracane są błędy sprawdzania poprawności i ostrzeżenia. Jeśli zawierającego przepływu pracy został utworzony za pomocą projektanta przepływów pracy, wszelkie błędy sprawdzania poprawności i ostrzeżenia są wyświetlane w projektancie. Jeśli przepływ pracy został utworzony poza projektanta przepływów pracy jakieś błędy sprawdzania poprawności są zwracane, gdy jest wywoływana przez przepływ pracy. Niezależnie od sposobu utworzenia przepływu pracy przepływ pracy z błędami sprawdzania poprawności nigdy nie można wykonać. Ta sekcja zawiera omówienie tych typów sprawdzania poprawności działania i sposób wywoływania sprawdzania poprawności działania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wymagane argumenty i grupy metod przeciążonych](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 Informacje dotyczące używania `RequiredArgument` i `OverloadGroup` atrybutów w celu udostępnienia weryfikacji.  
  
 [Weryfikacja opartej na kodzie imperatywne](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 Informacje dotyczące używania weryfikacji opartych na kodzie dla <xref:System.Activities.CodeActivity> i <xref:System.Activities.NativeActivity> na podstawie działań.  
  
 [Ograniczenia deklaratywne](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 Informacje dotyczące używania deklaratywne ograniczenia do udostępnienia weryfikacji działania złożonego.  
  
 [Wywoływanie sprawdzania poprawności działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 W tym artykule omówiono podczas sprawdzania poprawności działania jest wywoływana automatycznie oraz sposób jawnego wywołania sprawdzania poprawności.  
  
## <a name="reference"></a>Tematy pomocy  
  
## <a name="related-sections"></a>Sekcje pokrewne
