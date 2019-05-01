---
title: Kluczowe kwestie do zapamiętania
description: Pobierz najważniejsze wnioski z architektury Mikrousług .NET dla aplikacji kontenerowych nimi .NET przewodnik/książkę elektroniczną, zapewnienie krótkie omówienie ogólne problemy związane podczas korzystania z architektury mikrousług, takich jak zalety i wady, wzorców DDD projektu i rozwoju, a także odporności, zabezpieczeń i korzystanie z koordynatorów.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 90babf9a32d1e139216cbc8eb1c629401b8e83e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020182"
---
# <a name="key-takeaways"></a>Najważniejsze wnioski

Podsumowanie i najważniejsze wnioski poniżej przedstawiono najważniejsze wnioski z tego przewodnika.

**Korzyści z używania kontenerów.** Rozwiązania oparte na kontenerach zapewniają ważne oszczędności, ponieważ pomagają ograniczyć problemy z wdrażaniem spowodowanych błędami zależności w środowiskach produkcyjnych. Kontenery znacznie poprawić operacje operacji deweloperskich i produkcyjnych.

**Kontenery będą uniwersalnych.** Kontenery na platformie docker stają się de facto standardem w branży, obsługiwanych przez dostawców klucza w ekosystemów Windows i Linux, takie jak Microsoft, Amazon AWS, Google i IBM. Docker będzie prawdopodobnie wkrótce się wszechobecne w chmurze i lokalnych centrów danych.

**Kontenery jako jednostka wdrożenia.** Kontener platformy Docker, staje się standardową jednostką wdrożenia dla dowolnej usługi lub aplikacji opartej na serwerze.

**Mikrousługi.** Architektura mikrousług staje się preferowane podejście do rozproszonego, jak i dużych lub złożonych aplikacji o krytycznym znaczeniu oparte na wiele niezależnych podsystemów w formie autonomicznej usług. W przypadku opartych na mikrousługach architektury aplikacji została stworzona jako zbiór usług, które są rozwinięte, przetestowane, poddany kontroli wersji, wdrożyć i niezależne skalowanie. Każda usługa może obejmować wszystkie powiązane autonomicznej bazy danych.

**Projektowania opartego na domenie i SOA.** Wzorce architektury mikrousług pochodzi od dotycząca architektury zorientowanej na usługi (SOA) i projektowania opartego na domenach (DDD). Podczas projektowania i tworzenia mikrousług dla środowisk o zmieniających się potrzeb biznesowych i reguły należy wziąć pod uwagę podejścia DDD i wzorce.

**Wyzwania związane z Mikrousług.** Mikrousługi oferują wiele zaawansowane funkcje, takie jak niezależne wdrażanie, podsystem silnych granic i różnorodność technologii. Jednak mogą też wiązać się z wielu nowe wyzwania związane z tworzenia aplikacji rozproszonej, takie jak fragmentacji i modeli danych niezależnie od, odporne na błędy komunikacji między mikrousług, spójność i złożoność operacyjną, która wynika z agregowanie informacji rejestrowania i monitorowania z wielu mikrousług. Te aspekty wprowadzono wiele wyższego poziomu złożoności niż tradycyjna aplikacja monolityczna. W rezultacie tylko określone scenariusze są odpowiednie dla aplikacji opartych na mikrousługach. Obejmują one dużych i złożonych aplikacji za pomocą wiele podsystemów stale rosnących potrzeb. W takich przypadkach warto zainwestować w bardziej złożone architektury oprogramowania, ponieważ będzie ona lepiej długoterminowe elastyczność oraz obsługi aplikacji.

**Kontenery dla każdej aplikacji.** Kontenery są wygodne dla mikrousług, ale mogą być również przydatne w przypadku aplikacji monolitycznych oparte na tradycyjnych .NET Framework, korzystając z kontenerów Windows. Korzyści z używania platformy Docker, takich jak rozwiązywanie wielu problemów wdrażania do produkcji i dostarczanie z najnowocześniejszych środowiska deweloperskie i testowe, mają zastosowanie do wielu różnych typów aplikacji.

**Interfejs wiersza polecenia i środowisko IDE.** Za pomocą narzędzi firmy Microsoft można opracować konteneryzowanych aplikacji .NET przy użyciu metody. Można tworzyć przy użyciu interfejsu wiersza polecenia i środowisko oparte na Edytor przy użyciu interfejsu wiersza polecenia platformy Docker i Visual Studio Code. Lub za pomocą podejścia fokus w środowisku IDE programu Visual Studio i unikatowe funkcje tego programu dla platformy Docker, takich jak debugowanie obsługującej wiele kontenerów.

**Aplikacje w chmurze odporne na błędy.** W systemach opartych na chmurze i systemy rozproszone ogólnie rzecz biorąc, istnieje zawsze ryzyko częściowych niepowodzeń. Ponieważ klientów i usług są oddzielne procesy (kontenery), usługa nie może być przygotowane w sposób terminowy do żądania klienta. Na przykład usługa może być wyłączony z powodu błędu częściowego lub obsługi; Usługa może być przeciążona i odpowiada powoli do żądania; lub może nie być dostępne przez krótki czas ze względu na problemy z siecią. W związku z tym aplikacja w chmurze należy wykorzystywać te błędy i strategii, które umożliwią odpowiedzieć na te błędy. Strategie te mogą obejmować zasady ponawiania prób (ponowne wysyłanie wiadomości lub ponawiania żądań), i implementowanie wzorców wyłącznika w celu uniknięcia wykładniczego obciążenia powtarzanych żądań. Po prostu aplikacji działających w chmurze musi mieć elastyczne mechanizmy — zależnie od infrastruktury w chmurze lub niestandardowych, jak te wysokiego poziomu, dostarczonych przez dostawców ani koordynatorów magistrali usług.

**Zabezpieczenia.** Naszym współczesnym świecie kontenerów i mikrousług może narazić nowych luk w zabezpieczeniach. Istnieje kilka sposobów implementowania podstawowych zabezpieczeniach aplikacji, na podstawie uwierzytelniania i autoryzacji. Jednak zabezpieczenia kontenerów należy wziąć pod uwagę dodatkowe najważniejsze składniki, które powodują w aplikacjach z natury bezpieczniejszy. Krytyczne znaczenie dla tworzenia aplikacji pisanych małymi występują w bezpieczny sposób komunikowania się z innymi aplikacjami i systemami, coś, co często wymaga poświadczeń, tokeny, hasła i podobnych, nazywaną wpisów tajnych aplikacji. Żadne bezpieczne rozwiązanie, należy wykonać najlepszych rozwiązań dotyczących zabezpieczeń, takie jak szyfrowanie kluczy tajnych podczas przesyłanych i magazynowanych i zapobieganie kluczy tajnych przed wyciekiem, gdy używane przez gotowych aplikacji. Te potrzeby klucze tajne są przechowywane i przechowywać bezpiecznie, gdy za pomocą usługi Azure Key Vault.

**Orchestrators.** Oparte na kontenerach koordynatorów, takich jak usługi Azure Kubernetes Service i Azure Service Fabric są kluczową częścią wszelkie istotne mikrousług i aplikacji opartych na kontenerach. Te aplikacje pociąga za sobą wysokiego stopnia złożoności, potrzeb skalowalność i przejdź przez stałą ewolucji. Ten przewodnik wprowadził koordynatorów oraz ich rolę w przypadku rozwiązań opartych na mikrousługach i opartych na kontenerach. Jeśli wymagania w zakresie aplikacji przenosisz kierunku złożonych konteneryzowanych aplikacji, znajdziesz go przydatne do poszukiwania dodatkowe zasoby, aby uzyskać więcej informacji na temat koordynatorów.

>[!div class="step-by-step"]
>[Poprzednie](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)