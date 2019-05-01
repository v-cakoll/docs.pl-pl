---
ms.openlocfilehash: 1805c26f1eff46719f30de8a14ca6d35f01948a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640105"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Zmienna sterująca instrukcji foreach jest teraz o określonym zakresie w iteracji, więc zamknięcia przechwytywania semantyka jest inny (w języku C# 5)

|   |   |
|---|---|
|Szczegóły|Począwszy od C# 5 (Visual Studio 2012) <code>foreach</code> zmienne iteratora są ograniczone w iteracji. Może to spowodować przerwy, jeśli kod został wcześniej w zależności od zmiennych nie zostać zawarte w <code>foreach</code>jego zamknięciu. Objawem tej zmiany jest, że zmienna iteratora przekazywany do pełnomocnika jest traktowany jako wartość ma w tym czasie delegata zostanie utworzony, a nie wartość, która posiada w czasie, który obiekt delegowany jest wywoływany.|
|Sugestia|Najlepiej, jeśli kod powinien zostać zaktualizowany można oczekiwać, nowe zachowanie kompilatora. Jeśli stary semantyki są wymagane, zmienna sterująca można zastąpić przy użyciu oddzielnych zmienną, która jawnie znajduje się poza zakresem pętli.|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Przekierowanie|
