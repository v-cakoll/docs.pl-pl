---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617183"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>W wielowierszowym polu tekstowym ASP.Net TextBox zmieniły się odstępy w przypadku użycia klasy AntiXSSEncoder

#### <a name="details"></a>Szczegóły

W programie .NET Framework 4.0 dodatkowe wiersze były wstawiane między wierszami wielowierszowego pola tekstowego podczas ogłaszania zwrotnego w przypadku użycia klasy <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>. W wersji .NET Framework 4.5 te dodatkowe podziały wiersza nie są uwzględnione, ale tylko wtedy, gdy platformą docelową aplikacji internetowej jest program .NET Framework 4.5.

#### <a name="suggestion"></a>Sugestia

Należy pamiętać, że w aplikacjach sieci Web w wersji 4.0 przekierowanych na platformę .NET Framework 4.5 może wystąpić ulepszenie wielowierszowych pól tekstowych polegające na tym, że nie będą już wstawiane dodatkowe podziały wiersza. Jeśli nie jest to pożądane, aplikacja może przejawiać stare zachowanie podczas uruchamiania na platformie .NET Framework 4.5, o ile zostanie przekierowana do programu .NET Framework 4.0.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |
