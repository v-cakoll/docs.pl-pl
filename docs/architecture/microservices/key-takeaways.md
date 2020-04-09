---
title: Kluczowe kwestie do zapamiętania
description: Pobierz kluczowych wynos z architektury mikrousług .NET dla konteneryzowanych aplikacji .NET .NET przewodnik/e-book, aby szybko przyjrzeć się problemów wysokiego poziomu związanych podczas korzystania z architektury mikrousług, takich jak korzyści i wady, wzorce DDD do projektowania i rozwoju, a także odporność, zabezpieczenia i korzystanie z orchestrators.
ms.date: 10/19/2018
ms.openlocfilehash: 0e793a76fa59d6c131422480071d85ab3f18102c
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988781"
---
# <a name="key-takeaways"></a>Kluczowe dania na wynos

Jako podsumowanie i kluczowe dania na wynos, oto najważniejsze wnioski z tego przewodnika.

**Korzyści z używania kontenerów.** Rozwiązania oparte na kontenerach zapewniają istotne oszczędności kosztów, ponieważ pomagają zmniejszyć problemy z wdrażaniem spowodowane niepowodzeniem zależności w środowiskach produkcyjnych. Kontenery znacznie usprawniają operacje DevOps i produkcyjne.

**Pojemniki będą wszechobecne.** Kontenery oparte na platformie Docker stają się de facto standardem w branży, wspieranym przez kluczowych dostawców w ekosystemach Windows i Linux, takich jak Microsoft, Amazon AWS, Google i IBM. Docker prawdopodobnie wkrótce będzie wszechobecny zarówno w chmurach, jak i w lokalnych centrach danych.

**Kontenery jako jednostka wdrażania.** Kontener platformy Docker staje się standardową jednostką wdrażania dla dowolnej aplikacji lub usługi opartej na serwerze.

**Mikrousług.** Architektura mikrousług staje się preferowanym podejściem dla rozproszonych i dużych lub złożonych aplikacji o znaczeniu krytycznym opartych na wielu niezależnych podsystemach w postaci usług autonomicznych. W architekturze opartej na mikrousługach aplikacja jest zbudowana jako kolekcja usług, które są opracowywane, testowane, wersjonawane, wdrażane i skalowane niezależnie. Każda usługa może zawierać dowolną powiązaną autonomiczną bazę danych.

**Projektowanie oparte na domenie i SOA.** Wzorce architektury mikrousług wynikają z architektury zorientowanej na usługi (SOA) i projektowania opartego na domenie (DDD). Podczas projektowania i tworzenia mikrousług dla środowisk o zmieniających się potrzeb biznesowych i reguł, należy wziąć pod uwagę podejścia DDD i wzorców.

**Wyzwania mikrousług.** Mikrousługi oferują wiele zaawansowanych funkcji, takich jak niezależne wdrażanie, silne granice podsystemu i różnorodność technologii. Jednak również podnieść wiele nowych wyzwań związanych z rozproszonych tworzenia aplikacji, takich jak pofragmentowane i niezależne modele danych, odporne komunikacji między mikrousług, spójność ostateczna i złożoność operacyjna, która wynika z agregowania rejestrowania i monitorowania informacji z wielu mikrousług. Te aspekty wprowadzają znacznie wyższy poziom złożoności niż tradycyjna aplikacja monolityczna. W rezultacie tylko określone scenariusze są odpowiednie dla aplikacji opartych na mikrousługach. Należą do nich duże i złożone aplikacje z wieloma rozwijającymi się podsystemami. W takich przypadkach warto zainwestować w bardziej złożoną architekturę oprogramowania, ponieważ zapewni lepszą długoterminową elastyczność i konserwację aplikacji.

**Pojemniki do dowolnej aplikacji.** Kontenery są wygodne dla mikrousług, ale może być również przydatne dla aplikacji monolitycznych opartych na tradycyjnych .NET Framework, podczas korzystania z kontenerów systemu Windows. Korzyści wynikające z używania platformy Docker, takie jak rozwiązywanie wielu problemów związanych z wdrażaniem do produkcji i dostarczanie najnowocześniejszych środowisk deweloperskich i testowych, mają zastosowanie do wielu różnych typów aplikacji.

**CLI kontra IDE.** Za pomocą narzędzi firmy Microsoft można tworzyć konteneryzowane aplikacje .NET przy użyciu preferowanego podejścia. Można tworzyć za pomocą interfejsu wiersza polecenia i środowiska opartego na edytorze przy użyciu interfejsu wiersza polecenia platformy Docker i visual studio code. Lub można użyć podejścia skoncentrowanego na ideach z programem Visual Studio i jego unikatowych funkcji dla platformy Docker, takich jak debugowanie wielu kontenerów.

**Elastyczne aplikacje w chmurze.** W systemach chmurowych i systemach rozproszonych w ogóle zawsze istnieje ryzyko częściowej awarii. Ponieważ klienci i usługi są oddzielne procesy (kontenery), usługa może nie być w stanie odpowiedzieć w odpowiednim czasie na żądanie klienta. Na przykład usługa może być wyłączna z powodu częściowej awarii lub konserwacji; usługa może być przeciążona i odpowiadać powoli na żądania; lub może nie być dostępny przez krótki czas z powodu problemów z siecią. W związku z tym aplikacja oparta na chmurze musi obejmować te błędy i mają strategię w celu reagowania na te błędy. Strategie te mogą obejmować zasady ponawiania prób (ponowne wysłanie wiadomości lub ponawianie żądań) i implementowanie wzorców wyłącznika, aby uniknąć wykładniczego obciążenia powtarzających się żądań. Zasadniczo aplikacje oparte na chmurze muszą mieć odporne mechanizmy — oparte na infrastrukturze chmury lub niestandardowe, takie jak aplikacje wysokiego poziomu dostarczane przez koordynatorów lub magistrale usług.

**Zabezpieczeń.** Nasz nowoczesny świat kontenerów i mikrousług może ujawnić nowe luki w zabezpieczeniach. Istnieje kilka sposobów implementacji podstawowych zabezpieczeń aplikacji na podstawie uwierzytelniania i autoryzacji. Jednak zabezpieczenia kontenera należy wziąć pod uwagę dodatkowe składniki klucza, które powodują z natury bezpieczniejsze aplikacje. Kluczowym elementem tworzenia bezpieczniejszych aplikacji jest bezpieczny sposób komunikowania się z innymi aplikacjami i systemami, co często wymaga poświadczeń, tokenów, haseł i tym podobnych, powszechnie określanych jako wpisy tajne aplikacji. Każde bezpieczne rozwiązanie musi być zgodne z najlepszymi rozwiązaniami w zakresie zabezpieczeń, takimi jak szyfrowanie wpisów tajnych podczas przesyłania i w spoczynku oraz zapobieganie wyciekom wpisów tajnych po zużyciu przez aplikację końcową. Te wpisy tajne muszą być przechowywane i przechowywane bezpiecznie, tak jak podczas korzystania z usługi Azure Key Vault.

**Orkiestratorzy.** Orchestrators oparte na kontenerach, takich jak usługa Azure Kubernetes service i usługi Azure Service Fabric są kluczowym elementem wszelkich znaczących mikrousług i aplikacji opartych na kontenerze. Te aplikacje niosą ze sobą dużą złożoność, potrzeby skalowalności i przechodzą stałą ewolucję. W tym przewodniku wprowadzono koordynatorów i ich rolę w rozwiązaniach opartych na mikrousługach i kontenerach. Jeśli twoje potrzeby aplikacji są przenoszenie w kierunku złożonych konteneryzowanych aplikacji, znajdziesz warto szukać dodatkowych zasobów, aby dowiedzieć się więcej o koordynatorów.

>[!div class="step-by-step"]
>[Wstecz](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
