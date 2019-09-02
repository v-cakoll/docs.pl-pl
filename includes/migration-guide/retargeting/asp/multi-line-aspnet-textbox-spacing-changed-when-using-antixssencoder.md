---
ms.openlocfilehash: e2bca42daebd25667ab2f312d5e59089b986503c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640081"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>W wielowierszowym polu tekstowym ASP.Net TextBox zmieniły się odstępy w przypadku użycia klasy AntiXSSEncoder

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.0 dodatkowe wiersze były wstawiane między wierszami wielowierszowego pola tekstowego podczas ogłaszania zwrotnego w przypadku użycia klasy <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>. W wersji .NET Framework 4.5 te dodatkowe podziały wiersza nie są uwzględnione, ale tylko wtedy, gdy platformą docelową aplikacji internetowej jest program .NET Framework 4.5.|
|Sugestia|Należy pamiętać, że w aplikacjach sieci Web w wersji 4.0 przekierowanych na platformę .NET Framework 4.5 może wystąpić ulepszenie wielowierszowych pól tekstowych polegające na tym, że nie będą już wstawiane dodatkowe podziały wiersza. Jeśli nie jest to pożądane, aplikacja może przejawiać stare zachowanie podczas uruchamiania na platformie .NET Framework 4.5, o ile zostanie przekierowana do programu .NET Framework 4.0.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Przekierowanie|
