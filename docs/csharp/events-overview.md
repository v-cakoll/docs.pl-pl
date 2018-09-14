---
title: Wprowadzenie do zdarzeń
description: Dowiedz się więcej o zdarzeniach w .NET Core i cele projektu języka firmy Microsoft zdarzeń w tym omówieniu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 9f14954dd2e8aeacf3c5ae70a9e891ad11a6f0d7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618067"
---
# <a name="introduction-to-events"></a>Wprowadzenie do zdarzeń

[Poprzednie](delegates-patterns.md)

Zdarzenia są takie jak delegatów, *późnym wiązaniu* mechanizm. W rzeczywistości zdarzenia są tworzone na temat obsługi języków dla obiektów delegowanych.

Zdarzenia są sposób obiektowi emisji (do wszystkich zainteresowanych składników w systemie), że coś się stało. Jakikolwiek inny składnik może być subskrybowana przez zdarzenie, a otrzymasz powiadomienie, gdy wydarzenie jest podniesione.

Prawdopodobnie wykorzystano zdarzenia w niektórych z programowania. Wiele systemów graficzne mają model zdarzeń na interakcję z użytkownikiem raportu. Te zdarzenia będą raportów ruchów myszy, naciśnięcie przycisku i podobne interakcje. Jest to jeden z najbardziej typowych, ale na pewno nie tylko scenariusz użycia zdarzenia.

Można zdefiniować zdarzenia, które powinien być wywoływany dla swojej klasy. Ważnym zagadnieniem podczas pracy ze zdarzeniami jest to, że może być dowolny obiekt zarejestrowane dla określonego zdarzenia. Należy napisać kod, aby nie zgłaszała zdarzenia w przypadku odbiorników nie są skonfigurowane.

Subskrybowanie zdarzenia tworzy sprzężenie między dwoma obiektami (źródło zdarzenia i obiekt sink zdarzenia). Należy upewnić się, że obiekt sink zdarzenia anuluje subskrypcje ze źródła zdarzeń, gdy nie jest już są Państwo zainteresowani zdarzenia.

## <a name="design-goals-for-event-support"></a>Cele projektu do obsługi zdarzeń

Projektowanie języków dla zdarzeń jest przeznaczony dla tych celów.

Najpierw należy włączyć minimalny sprzężenia między źródłem zdarzeń i obiekt sink zdarzenia. Te dwa składniki nie może zapisywać w tej samej organizacji, a nawet mogą być aktualizowane zgodnie z harmonogramami coś zupełnie innego.

Po drugie powinny być bardzo prosty, aby subskrybować zdarzenia i zrezygnować z tego samego zdarzenia.

I wreszcie źródła zdarzeń powinien obsługiwać wielu subskrybentów zdarzeń. Powinien również obsługiwać, posiadające żadnych subskrybentów zdarzeń dołączonych.

Widać, że cele dotyczące zdarzenia są bardzo podobne do celów dla obiektów delegowanych.
Dlatego obsługę języka zdarzeń jest oparta na obsługę języka delegata.

## <a name="language-support-for-events"></a>Obsługa języka dla zdarzeń

Składnia służąca do definiowania zdarzenia, subskrypcji i anulowanie subskrypcji zdarzeń jest rozszerzeniem składni dla obiektów delegowanych.

Aby zdefiniować określone zdarzenie, możesz użyć `event` — słowo kluczowe:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Typ zdarzenia (`EventHandler<FileListArgs>` w tym przykładzie) musi być typem delegowanym. Istnieje szereg Konwencji, które należy wykonać podczas deklarowania zdarzenie. Zazwyczaj typ delegata zdarzenia ma zwracany typ void.
Deklaracje zdarzeń powinna być czasownikiem lub frazy zlecenie.
Użyj przeszłym (w tym przykładzie), gdy zdarzenie zgłasza coś, co się stało. Użyj zlecenie teraźniejszego (na przykład `Closing`) do zgłaszania coś, co się stanie. Często przy użyciu teraźniejszego wskazuje, że klasa obsługuje pewnego rodzaju dostosowywania zachowania. Jednym z najbardziej typowych scenariuszy jest aby zapewnić obsługę anulowania. Na przykład `Closing` zdarzeń może zawierać argument, który będzie wskazywać, jeśli operacja zamykania należy kontynuować, lub nie.  Inne scenariusze mogą umożliwiać wywołań zmodyfikować zachowanie, aktualizując właściwości argumentów zdarzenia. Może wywołać zdarzenie, aby wskazać proponowane następnej akcji, który zajmie algorytm. Program obsługi zdarzeń może uzasadniają różne akcje, modyfikując właściwości argumentu zdarzenia.

Jeśli chcesz zgłosić zdarzenie, wywołujesz procedury obsługi zdarzeń przy użyciu składni wywołania delegata:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Zgodnie z opisem w sekcji na [delegatów](delegates-patterns.md),?.
Operator ułatwia zapewnienie, że należy próbować zgłosić zdarzenie, gdy istnieją nie subskrybenci tego zdarzenia.
 
Subskrybowanie zdarzenia przy użyciu `+=` operator:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += onProgress;
```

Metody obsługi zwykle jest prefiksem "On" następuje nazwa zdarzenia, jak pokazano powyżej.

Anulowanie subskrypcji przy użyciu `-=` operator:

```csharp
lister.Progress -= onProgress;
```

Należy zauważyć, że uznana za zmienną lokalną dla wyrażenia, który reprezentuje program obsługi zdarzeń. Dzięki temu usuwa Anuluj subskrypcję programu obsługi.
Jeśli zamiast tego użyto treść wyrażenia lambda, którą chcesz usunąć program obsługi, który nigdy nie został dołączony, która nie wykonuje żadnych działań.

W następnym artykule dowiesz się więcej na temat zdarzeń typowych wzorców i różne odmiany w tym przykładzie.

[Next](event-pattern.md)
