---
title: Najważniejsze wnioski
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Najważniejsze wnioski
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d6e09b9856396e99c9b03d595c1896e2451724fe
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152266"
---
# <a name="key-takeaways"></a>Najważniejsze wnioski

Podsumowanie i najważniejsze wnioski poniżej przedstawiono najważniejsze wnioski z tego przewodnika.

**Korzyści z używania kontenerów.** Rozwiązania oparte na kontenerach zapewniają ważne korzyści wynikające z oszczędności kosztów, ponieważ kontenerów: czym są to rozwiązanie do problemów z wdrażaniem spowodowane brakiem zależności w środowiskach produkcyjnych. Kontenery znacznie poprawić operacje operacji deweloperskich i produkcyjnych.

**Kontenery będą uniwersalnych.** Kontenery na platformie docker stają się de facto standardem w branży kontenera, obsługiwane przez najważniejszych dostawców w ekosystemów Windows i Linux. W tym firmy Microsoft, Amazon AWS, Google i IBM. W najbliższej przyszłości Docker prawdopodobnie będzie wszechobecne w chmurze i lokalnych centrów danych.

**Kontenery jako jednostka wdrożenia.** Kontener platformy Docker, staje się standardową jednostką wdrożenia dla dowolnej usługi lub aplikacji opartej na serwerze.

**Mikrousługi.** Architektura mikrousług staje się preferowane podejście do rozproszonego i dużych lub złożonych aplikacji o krytycznym znaczeniu oparte na wiele niezależnych podsystemów w formie autonomicznej usług. W przypadku opartych na mikrousługach architektury aplikacji została stworzona jako kolekcja usług, które mogą być wywołane, przetestowane, poddany kontroli wersji, niezależne wdrażanie i skalowanie; może to obejmować wszystkie powiązane autonomicznej bazy danych.

**Projektowania opartego na domenie i SOA.** Wzorce architektury mikrousług pochodzi od dotycząca architektury zorientowanej na usługi (SOA) i projektowania opartego na domenach (DDD). Podczas projektowania i tworzenia mikrousług dla środowisk o zmieniających się reguł biznesowych, kształtowanie określonej domeny należy uwzględniać konto DDD podejścia i wzorce.

**Wyzwania związane z Mikrousług.** Mikrousługi oferują wiele zaawansowane funkcje, takie jak niezależne wdrażanie, podsystem silnych granic i różnorodność technologii. Jednak mogą też wiązać się z wielu nowe wyzwania związane z tworzenia aplikacji rozproszonej, takie jak fragmentacji i modeli danych niezależnie od, odporne na błędy komunikacji między mikrousług, spójność i złożoność operacyjną, która wynika z agregowanie informacji rejestrowania i monitorowania z wielu mikrousług. Te aspekty wprowadzają wyższego poziomu złożoności niż tradycyjna aplikacja monolityczna. W rezultacie tylko określone scenariusze są odpowiednie dla aplikacji opartych na mikrousługach. Obejmują one dużych i złożonych aplikacji za pomocą wiele podsystemów stale rosnących potrzeb; w takich przypadkach warto zainwestować w bardziej złożone architektury oprogramowania, ponieważ będzie ona lepiej długoterminowe elastyczność oraz obsługi aplikacji.

**Kontenery dla każdej aplikacji.** Kontenery są wygodne dla mikrousług, ale nie są wyłączne dla nich. Kontenery można również za pomocą aplikacji monolitycznej, w tym starsze aplikacje oparte na tradycyjnych .NET Framework i zmodernizowane za pośrednictwem kontenerów Windows. Korzyści z używania platformy Docker, takich jak rozwiązywanie wielu problemów wdrażania do produkcji i zapewniając najnowocześniejsze środowiska deweloperskie i testowe, mają zastosowanie do wielu różnych typów aplikacji.

**Interfejs wiersza polecenia i środowisko IDE.** Za pomocą narzędzi firmy Microsoft można opracować konteneryzowanych aplikacji .NET przy użyciu metody. Można tworzyć przy użyciu interfejsu wiersza polecenia i środowisko oparte na Edytor przy użyciu interfejsu wiersza polecenia platformy Docker i Visual Studio Code. Możesz też podejście skoncentrowane na IDE, za pomocą programu Visual Studio i unikatowe funkcje tego programu dla platformy Docker, takich jak np. możliwość debugować wielokontenerowe aplikacje.

**Aplikacje w chmurze odporne na błędy.** W systemach opartych na chmurze i systemy rozproszone ogólnie rzecz biorąc, istnieje zawsze ryzyko częściowych niepowodzeń. Ponieważ klientów i usług są oddzielne procesy (kontenery), usługa nie może być przygotowane w sposób terminowy do żądania klienta. Na przykład usługa może być wyłączony z powodu błędu częściowego lub obsługi; Usługa może być przeciążona i bardzo wolno do odpowiada żąda; lub może po prostu nie być dostępne przez krótki czas ze względu na problemy z siecią. W związku z tym aplikacja w chmurze należy wykorzystywać te błędy i strategii, które umożliwią odpowiedzieć na te błędy. Strategie te mogą obejmować zasady ponawiania prób (ponowne wysyłanie wiadomości lub ponawiania żądań), i implementowanie wzorców wyłącznika w celu uniknięcia wykładniczego obciążenia powtarzanych żądań. Po prostu aplikacji działających w chmurze musi mieć elastyczne mechanizmy — niestandardowe te lub takich, które jest oparte na infrastrukturze chmury, takie jak struktury wysokiego poziomu z koordynatorów lub magistrali usług.

**Zabezpieczenia.** Naszym współczesnym świecie kontenerów i mikrousług może narazić nowych luk w zabezpieczeniach. Podstawowa aplikacja zabezpieczeń opiera się na uwierzytelnianie i autoryzacja; istnieje wiele sposobów je zaimplementować. Jednak zabezpieczenia kontenerów obejmuje dodatkowe najważniejsze składniki, które powodują w aplikacjach z natury bezpieczniejszy. Krytyczne znaczenie dla tworzenia aplikacji pisanych małymi występują w bezpieczny sposób komunikowania się z innych aplikacji i systemów, coś, co oznacza często wymaga poświadczeń, tokeny, hasła i inne poufne informacje — zwykle określane jako wpisów tajnych aplikacji. Żadne bezpieczne rozwiązanie, należy wykonać najlepszych rozwiązań dotyczących zabezpieczeń, takie jak szyfrowanie kluczy tajnych przesyłanych; szyfrowanie kluczy tajnych przechowywanych; co uniemożliwia przypadkowo przeciek podczas używane przez aplikację końcowego wpisów tajnych. Te wpisy tajne muszą być przechowywane i zabezpieczenie, innym miejscu. Aby wzmocnić zabezpieczenia, możesz skorzystać wybranego koordynatora infrastruktury lub infrastruktury chmury, takich jak usługi Azure Key Vault i sposobów zapewnia kod aplikacji, które z niej korzystać.

**Koordynatorów.** Oparte na kontenerach koordynatorów, takich jak te dostępne w usłudze Azure Container Service (Kubernetes, Mesos DC/OS i Docker Swarm) i usługi Azure Service Fabric są niezbędne, dla każdej aplikacji opartych na mikrousługach gotowe do produkcji i wszelkie wielu kontenerów aplikacji przy użyciu znaczące złożoności, potrzeby skalowalności i rozwój stałej. Ten przewodnik wprowadził koordynatorów oraz ich rolę w przypadku rozwiązań opartych na mikrousługach i opartych na kontenerach. Jeśli wymagania w zakresie aplikacji przenosisz kierunku złożonych konteneryzowanych aplikacji, użytkownik będzie bardzo przydatne do poszukiwania dodatkowe zasoby, aby uzyskać więcej informacji na temat koordynatorów

>[!div class="step-by-step"]
>[Poprzednie](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)