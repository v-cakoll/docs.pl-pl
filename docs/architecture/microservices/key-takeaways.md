---
title: Kluczowe kwestie do zapamiętania
description: Pobierz kluczowe wynos z .NET Microservices Architecture for Containerized .NET Applications guide/e-book, aby szybko przyjrzeć się problemom wysokiego poziomu związanym z używaniem architektury mikrousług, takich jak korzyści i wady, wzorce DDD do projektowania i rozwoju, a także odporność, zabezpieczenia i korzystanie z koordynatorów.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296026"
---
# <a name="key-takeaways"></a>Kluczowe dania na wynos

Podsumowując i kluczowe dania na wynos, z tego przewodnika znajdują się najważniejsze wnioski.

**Zalety korzystania z kontenerów.** Rozwiązania oparte na kontenerach zapewniają ważne oszczędności kosztów, ponieważ pomagają zmniejszyć problemy z wdrażaniem spowodowane niepowodzeniem zależności w środowiskach produkcyjnych. Kontenery znacznie poprawić DevOps i operacji produkcyjnych.

**Kontenery będą wszechobecne.** Kontenery oparte na platformie Docker stają się de facto standardem w branży, wspieranym przez kluczowych dostawców w ekosystemach Windows i Linux, takich jak Microsoft, Amazon AWS, Google i IBM. Docker będzie prawdopodobnie wkrótce wszechobecne zarówno w chmurze i lokalnych centrów danych.

**Kontenery jako jednostka wdrożenia.** Kontener platformy Docker staje się standardową jednostką wdrożenia dla dowolnej aplikacji lub usługi opartej na serwerze.

**Mikrousług.** Architektura mikrousług staje się preferowanym podejściem dla rozproszonych i dużych lub złożonych aplikacji o znaczeniu krytycznym opartych na wielu niezależnych podsystemach w postaci usług autonomicznych. W architekturze opartej na mikrousługach aplikacja jest tworzona jako zbiór usług, które są opracowywane, testowane, wersjonowane, wdrażane i skalowane niezależnie. Każda usługa może zawierać dowolną powiązaną autonomiczną bazę danych.

**Projekt oparty na domenie i SOA.** Wzorce architektury mikrousług pochodzą z architektury zorientowanej na usługi (SOA) i projektowania opartego na domenie (DDD). Podczas projektowania i tworzenia mikrousług dla środowisk o zmieniających się potrzebach biznesowych i regułach, należy wziąć pod uwagę podejścia DDD i wzorce.

**Wyzwania mikrousług.** Mikrousługi oferują wiele zaawansowanych możliwości, takich jak niezależne wdrażanie, silne granice podsystemu i różnorodność technologii. Jednak również podnieść wiele nowych wyzwań związanych z tworzeniem aplikacji rozproszonych, takich jak rozdrobnionych i niezależnych modeli danych, odporne komunikacji między mikrousługami, spójność ostateczna i złożoność operacyjna, która wynika z agregowanie rejestrowania i monitorowania informacji z wielu mikrousług. Aspekty te wprowadzają znacznie wyższy poziom złożoności niż tradycyjne zastosowanie monolityczne. W rezultacie tylko określone scenariusze są odpowiednie dla aplikacji opartych na mikrousługach. Należą do nich duże i złożone aplikacje z wieloma ewoluującymi podsystemami. W takich przypadkach warto zainwestować w bardziej złożoną architekturę oprogramowania, ponieważ zapewni ona lepszą długoterminową elastyczność i konserwację aplikacji.

**Kontenery dla każdej aplikacji.** Kontenery są wygodne dla mikrousług, ale mogą być również przydatne w przypadku aplikacji monolitycznych opartych na tradycyjnej platformie .NET Framework podczas korzystania z kontenerów systemu Windows. Korzyści wynikające z używania platformy Docker, takie jak rozwiązywanie wielu problemów związanych z wdrażaniem do produkcji oraz zapewnienie najnowocześniejszych środowisk deweloperskich i testowych, dotyczą wielu różnych typów aplikacji.

**CLI kontra IDE.** Za pomocą narzędzi firmy Microsoft można tworzyć konteneryzowane aplikacje .NET przy użyciu preferowanego podejścia. Można tworzyć za pomocą cli i środowiska opartego na edytorze przy użyciu platformy Docker CLI i Visual Studio Code. Można też użyć podejścia zorientowanego na IDE z programu Visual Studio i jego unikatowych funkcji dla platformy Docker, takich jak debugowanie wielu kontenerów.

**Odporne aplikacje w chmurze.** W systemach opartych na chmurze i systemach rozproszonych w ogóle zawsze istnieje ryzyko częściowej awarii. Ponieważ klienci i usługi są oddzielnymi procesami (kontenerami), usługa może nie być w stanie odpowiedzieć w porę na żądanie klienta. Na przykład usługa może być w dół z powodu częściowej awarii lub konserwacji; usługa może być przeciążona i powoli odpowiadać na żądania; lub może nie być dostępny przez krótki czas z powodu problemów z siecią. W związku z tym aplikacja oparta na chmurze musi obejmować te błędy i mieć strategię w celu reagowania na te błędy. Strategie te mogą obejmować zasady ponawiania prób (ponowne wysyłanie wiadomości lub ponawianie żądań) i implementowanie wzorców wyłącznika, aby uniknąć wykładniczego obciążenia powtarzanych żądań. Zasadniczo aplikacje oparte na chmurze muszą mieć odporne mechanizmy — oparte na infrastrukturze chmury lub niestandardowe, jako aplikacje wysokiego poziomu dostarczane przez koordynatorów lub magistrale usług.

**Zabezpieczeń.** Nasz nowoczesny świat kontenerów i mikrousług może ujawnić nowe luki w zabezpieczeniach. Istnieje kilka sposobów implementowania podstawowych zabezpieczeń aplikacji na podstawie uwierzytelniania i autoryzacji. Jednak zabezpieczenia kontenera należy wziąć pod uwagę dodatkowe kluczowe składniki, które powodują z natury bezpieczniejsze aplikacje. Kluczowym elementem tworzenia bezpieczniejszych aplikacji jest bezpieczny sposób komunikowania się z innymi aplikacjami i systemami, co często wymaga poświadczeń, tokenów, haseł i tym podobnych, powszechnie nazywanych kluczami tajnymi aplikacji. Każde bezpieczne rozwiązanie musi być zgodne z najlepszymi rozwiązaniami dotyczącymi zabezpieczeń, takimi jak szyfrowanie kluczy tajnych podczas przesyłania i w stanie spoczynku oraz zapobieganie wyciekom tajnych podczas używania przez aplikację końcową. Te wpisy tajne muszą być przechowywane i przechowywane bezpiecznie, tak jak podczas korzystania z usługi Azure Key Vault.

**Orkiestratorzy.** Koordynatorów opartych na kontenerach, takich jak usługi Azure Kubernetes service i sieci szkieletowej usług Azure są kluczowym elementem wszystkich znaczących mikrousług i aplikacji opartych na kontenerach. Aplikacje te niosą ze sobą wysoką złożoność, potrzeby skalowalności i przechodzą przez stałą ewolucję. Ten przewodnik wprowadził koordynatorów i ich rolę w rozwiązaniach opartych na mikrousługach i kontenerach. Jeśli potrzeby aplikacji są przenoszenie w kierunku złożonych aplikacji konteneryzowanych, będzie przydatne do poszukiwania dodatkowych zasobów, aby dowiedzieć się więcej o koordynatorów.

>[!div class="step-by-step"]
>[Wstecz](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
