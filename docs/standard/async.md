---
title: Async — omówienie
description: Dowiedz się, jak programowania asynchronicznego to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9084da80ff400bf99fc8641c69bc38c805d039a
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071435"
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

Aby uzyskać więcej informacji, zobacz [Async szczegółowo](async-in-depth.md) tematu.

[Wzorce programowania asynchronicznego](asynchronous-programming-patterns/index.md) temat zawiera omówienie trzy wzorce programowania asynchronicznego obsługiwane w środowisku .NET:  
  
-   [Asynchroniczne programowania modelu (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starsze)  
  
-   [Oparty na zdarzeniach asynchroniczny wzorzec (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starsze)  
  
-   [Oparty na zadaniach asynchronicznej wzorca (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (zalecane w przypadku nowych wdrożeń)  

Aby uzyskać więcej informacji na temat zalecanych model programowania opartego na zadaniach, zobacz [programowania asynchronicznego opartego na zadaniach](parallel-programming/task-based-asynchronous-programming.md) tematu.
