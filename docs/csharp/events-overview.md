---
title: Wprowadzenie do zdarzeń
description: Więcej informacji na temat zdarzeń w .NET Core i cele firmy Microsoft projektu języka zdarzeń w tym omówieniu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 2a2230ea5fba1b0cd5b13319677965e7a776549e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-events"></a>Wprowadzenie do zdarzeń

[Poprzednie](delegates-patterns.md)

Zdarzenia są takie jak delegatów, *późne wiązanie* mechanizmu. W rzeczywistości zdarzenia są tworzone na obsługę języka delegatów.

Zdarzenia są sposób dla obiekt emisji (wszystkich zainteresowanych składników w systemie) szukają miało miejsce. Drugim składnikiem mogą subskrybować zdarzenia i powiadomienia, gdy zdarzenie jest wywoływane.

W niektórych z programowania prawdopodobnie używano zdarzenia. Wiele systemów graficznego ma modelu zdarzeń do interakcji z użytkownikiem raportu. Te zdarzenia rozpoczną przesyłanie raportów o ruchów myszy, naciśnięcie przycisku i podobne interakcji. Który jest jednym z najbardziej typowych, ale na pewno nie jedyny scenariusz, w którym zdarzenia są używane.

Możesz definiować zdarzenia, które powinny być wywoływane dla klas. Ważnym zagadnieniem podczas pracy ze zdarzeniami jest to, że może być dowolny obiekt zarejestrowane dla określonego zdarzenia. Należy napisać kod, aby nie zgłaszał zdarzenia, gdy nie odbiorników są skonfigurowane.

Subskrybowanie zdarzeń tworzy sprzężenia między dwoma obiektami (źródło zdarzeń i obiekt sink zdarzenia). Należy się upewnić, że obiekt sink zdarzenia, cofnięć subskrypcji z źródło zdarzeń, gdy nie jest już zainteresowani zdarzenia.

## <a name="design-goals-for-event-support"></a>Cele projektowania obsługi zdarzeń

Język projektu dla zdarzeń jest przeznaczony dla tych celów.

Najpierw włączyć minimalne sprzężenia między źródłem zdarzenia i obiekt sink zdarzenia. Te dwa składniki nie może zapisywać w tej samej organizacji, a nawet może zostać zaktualizowany w całkowicie różnych harmonogramów.

Po drugie powinny być bardzo proste, aby subskrybować zdarzenia i można zrezygnować z tego samego zdarzenia.

A na koniec źródła zdarzeń powinny obsługiwać wielu subskrybentów zdarzeń. Należy również obsługiwać, o subskrybentów zdarzeń dołączony.

Widać, że cele dotyczące zdarzenia są bardzo podobne do celów dla obiektów delegowanych.
Dlatego obsługa języków zdarzeń jest oparty na obsługę języka delegata.

## <a name="language-support-for-events"></a>Obsługa języka dla zdarzenia

Składnia definiowanie zdarzeń, subskrypcja i anulowanie subskrypcji zdarzeń jest rozszerzeniem składni delegatów.

Aby zdefiniować zdarzenia używane `event` — słowo kluczowe:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Typ zdarzenia (`EventHandler<FileListArgs>` w tym przykładzie) musi być typem obiektu delegowanego. Istnieje wiele Konwencji, które należy wykonać przy deklarowaniu zdarzenia. Zazwyczaj typ delegata zdarzenia ma typ zwracany typ void.
Deklaracje zdarzeń powinny być zlecenie lub frazę zlecenia.
Użyj przeszłego (w tym przykładzie), gdy zdarzenie zgłasza rzecz, która została wykonana. Użyj polecenia teraźniejszym (na przykład `Closing`) do zgłaszania coś, co się stanie. Często przy użyciu teraźniejszym wskazuje, że klasa obsługuje określonego rodzaju zachowanie dostosowania. Jednym z najbardziej typowych scenariuszy jest obsługuje anulowania. Na przykład `Closing` zdarzeń może zawierać argumentu, który wskazuje, czy operacja zamykania powinno być kontynuowane, czy nie.  Inne scenariusze mogą umożliwić wywołującym zmodyfikować zachowanie, aktualizując właściwości argumentów zdarzenia. Mogą zgłaszać zdarzenia w celu poinformowania proponowanych następnej akcji zajmie algorytmu. Program obsługi zdarzeń może wprowadzić różne akcje przez modyfikowanie właściwości argumentu zdarzenia.

Jeśli chcesz zgłosić zdarzenie, należy wywołać przy użyciu składni wywołania obiektu delegowanego obsługi zdarzeń:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Zgodnie z opisem w sekcji na [delegatów](delegates-patterns.md),?.
Operator ułatwia zapewnienie, że należy próbować zgłosić zdarzenie, gdy nie ma żadnych subskrybentów tego zdarzenia.
 
Subskrybowanie zdarzeń za pomocą `+=` operator:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

Metoda obsługi zwykle jest prefiksem "Na" następuje nazwa zdarzenia opisane powyżej.

Anulowanie subskrypcji przy użyciu `-=` operator:

```csharp
lister.Progress -= onProgress;
```

Należy pamiętać, że zadeklarowany jako zmienna lokalna dla wyrażenia, który reprezentuje program obsługi zdarzeń. Dzięki temu usuwa anulowania subskrypcji programu obsługi.
Jeśli zamiast tego użyto treści wyrażenia lambda, próbujesz usunąć program obsługi, który nigdy nie został dołączony, które nie działają.

W kolejnym artykule dowiesz się więcej na temat wzorców typowych zdarzeń i różnych zmian w tym przykładzie.

[Next](event-pattern.md)
