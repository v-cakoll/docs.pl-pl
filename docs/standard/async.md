---
title: "Async — omówienie"
description: "Dowiedz się, jak programowania asynchronicznego to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy."
keywords: .NET, .NET core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f2dddc21dfb124fe97c397a156743981a67e4037
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="async-overview"></a>Async — omówienie

Nie tak dawno temu aplikacje otrzymano szybciej po prostu przy zakupie nowszej komputerze lub serwerze, a następnie tego trendu zatrzymana. W rzeczywistości wycofać. Telefony komórkowe pojawił się z 1ghz pojedynczego rdzenia ARM mikroukłady i obciążenia serwera są przenoszone do maszyn wirtualnych. Użytkownicy nadal mają reakcje interfejsu użytkownika, a właściciele firm serwerów, które firmy. Przejście do przenośnych i chmury i podłączonej do Internetu populacji > Użytkownicy 3B spowodowało nowy zestaw wzorców oprogramowania. 

* Aplikacje klienckie powinny być zawsze włączone, zawsze połączone i stale reakcji do interakcji z użytkownikiem (na przykład touch) z klasyfikacji magazynu wysoka!
* Usługi powinny obsługiwać największego ruchu przez bezpiecznie skalowanie w górę i w dół. 

Programowanie asynchroniczne to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy. .NET oferuje możliwość reakcji i elastycznych z łatwy w użyciu, poziom języka asynchroniczne modele programowania w języku C#, VB i F # dla aplikacji i usług.

## <a name="why-write-async-code"></a>Dlaczego należy pisać kod Async?

Nowoczesne aplikacje należy zwiększone użycie operacji We/Wy plików i sieci. W efekcie niską użytkowników oraz wykorzystanie sprzętu, chyba że chcesz nauczenia i używania trudne wzorce API we/wy tradycyjnie bloku domyślnie. Oparty na zadaniach asynchronicznej interfejsów API i model programowania asynchronicznego poziom języka Odwróć tego modelu, co wykonanie asynchroniczne domyślnej z kilku nowych pojęć, aby dowiedzieć się więcej.

Kod Async ma następującą charakterystykę:

* Obsługuje więcej żądań serwera według reaguje wątków do obsługi żądań więcej podczas oczekiwania na żądań We/Wy do zwrócenia.
* Umożliwia UI być bardziej elastyczny przez reaguje wątków interakcja interfejsu użytkownika podczas oczekiwania na we/wy żądań i przechodzenia długotrwałe pracy innych rdzeni Procesora.
* Wiele nowszej interfejsów API architektury .NET jest asynchroniczne.
* Jest łatwy do pisania kodu asynchronicznych w .NET!

## <a name="whats-next"></a>Co to jest dalej?

Nowości w asynchronicznej pojęcia i programowania w języku, dla [Async szczegółowo](async-in-depth.md) i [programowania asynchronicznego opartego na zadaniach](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).
