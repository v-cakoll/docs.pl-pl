---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617305"
---
### <a name="workflow-30-types-are-obsolete"></a>Typy przepływów pracy w wersji 3.0 są przestarzałe

#### <a name="details"></a>Szczegóły

Interfejsy API programu Windows Workflow Foundation (WWF) 3.0 (te z przestrzeni nazw System.Workflow) są obecnie przestarzałe.

#### <a name="suggestion"></a>Sugestia

Zamiast nich należy używać nowych interfejsów API programu WWF 4.0 (w System.Activities). Przykład korzystania z nowych interfejsów API można znaleźć [tutaj](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), a dalsze wskazówki są dostępne [tutaj](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5). Ponieważ interfejsy API WWF 3.0 są nadal obsługiwane, alternatywnym rozwiązaniem może być używanie ich i pominięcie ostrzeżenia podczas kompilacji lub użycie starszego kompilatora.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |
