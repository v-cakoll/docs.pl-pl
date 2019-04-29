---
title: Async — omówienie
description: Dowiedz się, jak programowanie async technika sprawia, że prosta do obsługi blokowania We/Wy i jednoczesnych operacji na wiele rdzeni.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9084da80ff400bf99fc8641c69bc38c805d039a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627908"
---
# <a name="async-overview"></a>Async — omówienie

Nie tak dawno temu aplikacje szybciej po prostu kupując nowszej komputer lub serwer, a następnie ten trend zatrzymano usługę. W rzeczywistości odwrócona. Telefony komórkowe pojawiły się o 1ghz jednordzeniowy ARM mikroukładami i obciążenia serwera są przenoszone do maszyn wirtualnych. Użytkownicy nadal mają dynamicznym interfejsie użytkownika i właściciele firm ma serwerów, które można skalować z działalności. Przejścia dla urządzeń przenośnych i chmury i podłączonej do Internetu populacji > Użytkownicy 3B spowodowało nowy zestaw wzorców oprogramowania. 

* Aplikacje klienckie powinny być zawsze włączone zawsze połączone i stale elastyczna na interakcję z użytkownikiem (na przykład touch) przy użyciu klasyfikacji magazynu wysoka!
* Usługi powinny obsługiwać skokami ruchu, bez problemu zmieniała skalując w górę i w dół. 

Programowanie asynchroniczne to technika sprawia, że prosta do obsługi blokowania We/Wy i jednoczesnych operacji na wiele rdzeni. .NET zapewnia możliwość dynamicznego i elastyczne z łatwe w użyciu, poziom języka programowania modelami asynchronicznymi w dla aplikacji i usług C#, VB i F#.

## <a name="why-write-async-code"></a>Dlaczego należy pisać kod asynchroniczny?

Nowoczesne aplikacje należy zwiększone użycie operacji We/Wy plików i sieci. Interfejsów API we/wy tradycyjnie Blokuj domyślnie powodujące niską użytkowej oraz wykorzystania zasobów sprzętowych, chyba że chcesz do nauczenia i używania pokonywania wyzwań wynikających ze wzorców. Oparta na zadaniach asynchronicznej interfejsów API i model programowania asynchronicznego poziomu języka Odwróć ten model, dzięki czemu wykonanie asynchroniczne domyślnej z kilku nowych pojęć, aby dowiedzieć się więcej.

Kod asynchroniczny ma następującą charakterystykę:

* Obsługuje więcej żądań serwera według reaguje wątków może obsługiwać więcej żądania podczas oczekiwania na żądań We/Wy do zwrócenia.
* Umożliwia UI większą responsywność reaguje wątków interakcja interfejsu użytkownika podczas oczekiwania na We/Wy i przechodzenie długotrwała praca, inne rdzeni procesora CPU.
* Wiele z nowszych interfejsów API platformy .NET są asynchroniczne.
* To ułatwia pisanie kodu asynchronicznego w .NET!

## <a name="whats-next"></a>Co dalej?

Aby uzyskać więcej informacji, zobacz [Async szczegółowo](async-in-depth.md) tematu.

[Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) temat zawiera omówienie trzech asynchronicznych wzorcach programowania, obsługiwane na platformie .NET:  
  
- [Modelu programowania asynchronicznego (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starsza wersja)  
  
- [Oparte na zdarzeniach asynchroniczny wzorzec (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starsza wersja)  
  
- [Oparta na zadaniach asynchronicznej wzorca (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (zalecane w przypadku nowych wdrożeń)  

Aby uzyskać więcej informacji na temat zalecanych modelu programowania opartego na zadaniach, zobacz [programowania asynchronicznego opartego na zadaniach](parallel-programming/task-based-asynchronous-programming.md) tematu.
