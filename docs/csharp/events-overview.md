---
title: Wprowadzenie do zdarzeń
description: Dowiedz się więcej o wydarzeniach w .NET Core i naszych celach projektowania języka dla wydarzeń w tym przeglądzie.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 4e660f85eecfd5668919baf21a0d26f858faf5a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146117"
---
# <a name="introduction-to-events"></a>Wprowadzenie do zdarzeń

[Wstecz](delegates-patterns.md)

Zdarzenia są, podobnie jak delegaci, mechanizm *późnego wiązania.* W rzeczywistości zdarzenia są zbudowane na obsługę języka dla delegatów.

Zdarzenia są sposobem na obiekt do emisji (do wszystkich zainteresowanych składników w systemie), że coś się stało. Każdy inny składnik może subskrybować zdarzenie i otrzymywać powiadomienia o wysuwaniu zdarzenia.

Prawdopodobnie używałeś zdarzeń w niektórych programach. Wiele systemów graficznych ma model zdarzeń do raportowania interakcji użytkownika. Zdarzenia te będą raportować ruch myszy, naciśnięcia przycisków i podobne interakcje. Jest to jeden z najczęstszych, ale z pewnością nie jedyny scenariusz, w którym są używane zdarzenia.

Można zdefiniować zdarzenia, które powinny być wywoływane dla klas. Jedną z ważnych kwestii podczas pracy ze zdarzeniami jest to, że nie może być żadnego obiektu zarejestrowanego dla określonego zdarzenia. Należy napisać kod, aby nie zgłaszał zdarzenia, gdy nie są skonfigurowane odbiorniki.

Subskrybowanie zdarzenia tworzy również sprzężenie między dwoma obiektami (źródłem zdarzeń i ujściem zdarzenia). Należy upewnić się, że sink zdarzenia anulują subskrypcję ze źródła zdarzeń, gdy nie są już zainteresowani wydarzeniami.

## <a name="design-goals-for-event-support"></a>Cele projektowe dla obsługi zdarzeń

Projekt języka dla zdarzeń jest przeznaczony dla następujących celów:

- Włącz bardzo minimalne sprzężenie między źródłem zdarzeń a pochłaniaczem zdarzeń. Te dwa składniki mogą nie być zapisywane przez tę samą organizację, a nawet mogą być aktualizowane według zupełnie innych harmonogramów.

- Subskrypcja wydarzenia powinna być bardzo prosta i rezygnacja z subskrypcji tego samego wydarzenia.

- Źródła zdarzeń powinny obsługiwać wielu subskrybentów zdarzeń. Powinien również obsługiwać brak subskrybenów zdarzeń.

Widać, że cele dla wydarzeń są bardzo podobne do celów dla delegatów.
Dlatego obsługa języka zdarzenia jest zbudowana na obsłudze języka delegata.

## <a name="language-support-for-events"></a>Obsługa językowa wydarzeń

Składnia definiowania zdarzeń oraz subskrybowania lub cofania subskrypcji ze zdarzeń jest rozszerzeniem składni delegatów.

Aby zdefiniować zdarzenie, `event` użyjesz słowa kluczowego:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Typ zdarzenia (`EventHandler<FileListArgs>` w tym przykładzie) musi być typem delegata. Istnieje wiele konwencji, które należy wykonać podczas deklarowania zdarzenia. Zazwyczaj typ delegata zdarzenia ma zwrot void.
Deklaracje zdarzeń powinny być czasownikiem lub wyrażeniem czasownika.
Użyj czasu przeszłego, gdy zdarzenie zgłasza coś, co się stało. Użyj czasownika czasu teraźniejszego (na przykład), aby zgłosić coś, `Closing`co ma się wydarzyć. Często przy użyciu czasu teraźniejszego wskazuje, że klasa obsługuje pewnego rodzaju zachowanie dostosowywania. Jednym z najczęstszych scenariuszy jest obsługa anulowania. Na przykład `Closing` zdarzenie może zawierać argument, który wskazywałby, czy operacja zamknięcia powinna być kontynuowana, czy nie.  Inne scenariusze mogą umożliwić wywołującym zmodyfikować zachowanie, aktualizując właściwości argumentów zdarzenia. Możesz zgłosić zdarzenie, aby wskazać proponowaną następną akcję, którą podejmie algorytm. Program obsługi zdarzeń może nakazać inną akcję, modyfikując właściwości argumentu zdarzenia.

Jeśli chcesz podnieść zdarzenie, należy wywołać programy obsługi zdarzeń przy użyciu składni wywołania delegata:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Jak omówiono w sekcji na [delegatów](delegates-patterns.md), ?.
operator ułatwia zapewnienie, że nie próbujesz podnieść zdarzenie, gdy nie ma żadnych subskrybentów tego zdarzenia.

Subskrybujesz wydarzenie `+=` za pomocą operatora:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

Metoda obsługi zazwyczaj ma prefiks "On", po którym następuje nazwa zdarzenia, jak pokazano powyżej.

Zrezygnacje z subskrypcji za pomocą `-=` operatora:

```csharp
fileLister.Progress -= onProgress;
```

Należy pamiętać, że zadeklarowałem zmienną lokalną dla wyrażenia reprezentującego program obsługi zdarzeń. Dzięki temu anulowanie subskrypcji usuwa program obsługi.
Jeśli zamiast tego użyto treści wyrażenia lambda, próbujesz usunąć program obsługi, który nigdy nie został dołączony, co nic nie robi.

W następnym artykule dowiesz się więcej o typowych wzorcach zdarzeń i różnych odmianach tego przykładu.

[Dalej](event-pattern.md)
