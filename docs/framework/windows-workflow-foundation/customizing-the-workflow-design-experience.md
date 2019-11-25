---
title: Dostosowywanie środowiska projektowania przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 41be55391ae9481f6c2e4feb76443f7fb676b69d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141929"
---
# <a name="customizing-the-workflow-design-experience"></a>Dostosowywanie środowiska projektowania przepływu pracy

Scenariusze projektowania działań niestandardowych i przeprowadzenia [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] są znacznie uproszczone w .NET Framework 4. Opracowywanie i wdrażanie jest teraz łatwiejsze i bardziej elastyczne. Infrastruktury Key Change polega na tym, że nowy model programowania projektanta działań jest oparty na Windows Presentation Foundation (WPF). Dzięki temu można z łatwością definiować projektantów działań i ponownie hostować [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w innych aplikacjach z porównywalną. Podczas rehostowania można opracować Edytor wyrażeń niestandardowych do obsługi technologii IntelliSense lub uproszczonej domeny wyrażeń. Integracja z usługą Windows Communication Foundation (WCF) stała się bardziej bezproblemowe dzięki użyciu usług przepływu pracy. Projektanci działań niestandardowych i drzewo elementów modelu mogą służyć do ulepszania środowiska projektowania dla projektantów przepływów pracy.

## <a name="in-this-section"></a>W tej sekcji

 [Używanie niestandardowych szablonów i projektantów działań](using-custom-activity-designers-and-templates.md)

 Opisuje sposób tworzenia nowych projektantów i szablonów działań niestandardowych.

 [Rehostowanie projektanta przepływu pracy](rehosting-the-workflow-designer.md)

 Opisuje, jak ponownie hostować [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] poza programem Visual Studio oraz jak wyświetlać błędy walidacji.

 [Używanie edytora wyrażeń niestandardowych](using-a-custom-expression-editor.md)

 Zawiera opis sposobu implementowania niestandardowego edytora wyrażeń do użycia z projektantami przepływu pracy przemieszczonymi poza programem Visual Studio 2010.

## <a name="reference"></a>Tematy pomocy

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie programu Windows Workflow Foundation](extend.md)
- [Projektant](./samples/designer.md)
- [Projektanci działań niestandardowych](./samples/custom-activity-designers.md)
- [Rehostowanie projektanta](./samples/designer-rehosting.md)
