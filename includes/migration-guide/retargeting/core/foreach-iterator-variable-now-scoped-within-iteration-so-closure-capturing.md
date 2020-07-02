---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617197"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Zmienna iteratora foreach jest teraz objęta zakresem iteracji, więc semantyka przechwytywania zamknięć jest różna (w języku C# 5)

#### <a name="details"></a>Szczegóły

Począwszy od języka C# 5 (Visual Studio 2012), `foreach` zmienne iteratora są objęte zakresem iteracji. Może to spowodować przerwanie, jeśli kod był wcześniej w zależności od zmiennych, które nie zostaną uwzględnione w `foreach` zamknięciu. Objawem tej zmiany jest to, że zmienna iteratora przeniesiona do delegata jest traktowana jako wartość, którą ma w momencie utworzenia delegata, a nie wartość, która ma w momencie wywołania obiektu delegowanego.

#### <a name="suggestion"></a>Sugestia

W idealnym przypadku należy zaktualizować kod, aby oczekiwać na nowe zachowanie kompilatora. Jeśli stara semantyka jest wymagana, zmienna iteratora może zostać zastąpiona oddzielną zmienną, która jest jawnie umieszczona poza zakresem pętli.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |
