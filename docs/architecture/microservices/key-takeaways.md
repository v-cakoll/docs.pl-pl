---
title: Kluczowe kwestie do zapamiętania
description: Pobierz usługę Key wnioski z architektury mikrousług platformy .NET dla przewodnika lub książki elektronicznej platformy .NET, aby szybko zapoznać się z ogólnymi problemami związanymi z korzystaniem z architektury mikrousług, takich jak korzyści i wady, wzorce dotyczące projektowania i programowanie, a także odporność, bezpieczeństwo i korzystanie z koordynatorów.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296026"
---
# <a name="key-takeaways"></a>Wnioski Key

Jako podsumowanie i usługi Key wnioski, poniżej przedstawiono najważniejsze wnioski z tego przewodnika.

**Zalety korzystania z kontenerów.** Rozwiązania oparte na kontenerach zapewniają ważne oszczędności, ponieważ zmniejszają one problemy związane z wdrażaniem spowodowane awarią zależności w środowiskach produkcyjnych. Kontenery znacząco ulepszają operacje DevOps i produkcyjne.

**Kontenery będą powszechne.** Kontenery oparte na platformie Docker stają się niefaktycznym standardem w branży, obsługiwane przez kluczowych dostawców w ekosystemach systemów Windows i Linux, takich jak Microsoft, Amazon AWS, Google i IBM. Platforma Docker prawdopodobnie wkrótce będzie w chmurze i lokalnych centrach danych.

**Kontenery jako jednostkę wdrożenia.** Kontener platformy Docker staje się standardową jednostką wdrożenia dla dowolnej aplikacji lub usługi opartej na serwerze.

**Mikrousług.** Architektura mikrousług jest preferowanym podejściem dla rozproszonych i dużych lub złożonych aplikacji o znaczeniu strategicznym w oparciu o wiele niezależnych podsystemów w formie usług autonomicznych. W architekturze mikrousług aplikacja jest zbudowana jako kolekcja usług, które są opracowywane, testowane, wdrażane i skalowane niezależnie. Każda usługa może zawierać dowolną powiązaną autonomiczną bazę danych.

**Projektowanie i SOA oparte na domenie.** Wzorce architektury mikrousług pochodzą z architektury zorientowanej na usługi (SOA) i projektu opartego na domenie (DDD). Podczas projektowania i opracowywania mikrousług dla środowisk z rosnącymi potrzebami i regułami biznesowymi należy wziąć pod uwagę metody i wzorce.

**Wyzwania dla mikrousług.** Mikrousługi oferują wiele zaawansowanych możliwości, takich jak niezależne wdrażanie, silne podsystemy i różnorodność technologii. Jednak mogą oni również zgłaszać wiele nowych wyzwań związanych z tworzeniem aplikacji rozproszonych, takimi jak pofragmentowane i niezależne modele danych, odporna komunikacja między mikrousługami, spójnością ostateczną i złożonością operacyjną, która wynika z Agregowanie informacji o rejestrowaniu i monitorowaniu z wielu mikrousług. Te aspekty wprowadzają znacznie wyższy poziom złożoności niż tradycyjna aplikacja monolityczna. W związku z tym tylko określone scenariusze są odpowiednie dla aplikacji opartych na mikrousługach. Obejmują one duże i złożone aplikacje z wieloma rozwojem podsystemów. W takich przypadkach warto zainwestować w bardziej złożoną architekturę oprogramowania, ponieważ zapewni to lepszą długoterminową elastyczność i konserwację aplikacji.

**Kontenery dla dowolnej aplikacji.** Kontenery są wygodne dla mikrousług, ale mogą być również przydatne w przypadku aplikacji monolitycznych opartych na tradycyjnych .NET Framework w przypadku korzystania z kontenerów systemu Windows. Zalety korzystania z platformy Docker, takich jak rozwiązywanie wielu problemów z wdrażaniem w środowisku produkcyjnym oraz dostarczanie najnowocześniejszych środowisk deweloperskich i testowych, mają zastosowanie do wielu różnych typów aplikacji.

**Interfejs wiersza polecenia i środowisko IDE.** Za pomocą narzędzi firmy Microsoft można opracowywać kontenery aplikacji platformy .NET przy użyciu preferowanego podejścia. Można tworzyć za pomocą interfejsu wiersza polecenia i środowiska opartego na edytorze przy użyciu interfejsu wiersza polecenia platformy Docker i Visual Studio Code. Można też użyć podejścia ukierunkowanego na środowisko IDE z programem Visual Studio i jego unikatowymi funkcjami dla platformy Docker, takich jak debugowanie z użyciem kilku kontenerów.

**Odporne aplikacje w chmurze.** W systemach opartych na chmurze i w systemach rozproszonych ogólnie istnieje ryzyko częściowej awarii. Ponieważ klienci i usługi są oddzielnymi procesami (kontenerami), usługa może nie być w stanie odpowiedzieć w odpowiednim czasie na żądanie klienta. Na przykład usługa może nie działać z powodu częściowej awarii lub konserwacji; Usługa może być przeciążona i reagować na żądania; lub może być niedostępna przez krótki czas ze względu na problemy z siecią. W związku z tym aplikacje oparte na chmurze muszą obejmować te awarie i mieć strategię w celu reagowania na te awarie. Strategie te mogą obejmować zasady ponawiania (wysyłanie komunikatów lub ponawianie żądań) i implementowanie wzorców wyłącznika, aby uniknąć wykładniczego ładowania powtarzających się żądań. Zasadniczo aplikacje oparte na chmurze muszą mieć odporne na awarie mechanizmy — na podstawie infrastruktury chmurowej lub niestandardowej, jako wysokiego poziomu udostępniane przez usługi Orchestrator lub autobusy usług.

**Bezpieczeństw.** Nasz współczesny światowy kontenery i mikrousługi mogą uwidaczniać nowe luki w zabezpieczeniach. Istnieje kilka sposobów implementacji podstawowych zabezpieczeń aplikacji na podstawie uwierzytelniania i autoryzacji. Jednak zabezpieczenia kontenerów muszą uwzględniać dodatkowe kluczowe składniki, które powodują, że są to bezpieczne aplikacje. Krytyczny element tworzenia bezpieczniejszej aplikacji ma bezpieczny sposób komunikowania się z innymi aplikacjami i systemami, co często wymaga poświadczeń, tokenów, haseł i podobnych, często określanych jako wpisy tajne aplikacji. Każde bezpieczne rozwiązanie musi być zgodne z najlepszymi rozwiązaniami w zakresie bezpieczeństwa, takimi jak szyfrowanie wpisów tajnych podczas przesyłania i przechowywania oraz zapobieganie wyciekom kluczy, które są używane przez aplikację końcową. Te klucze tajne muszą być przechowywane i przechowywane bezpiecznie, tak jak w przypadku korzystania z Azure Key Vault.

**Koordynatorów.** W przypadku programów Orchestrator opartych na kontenerach, takich jak Azure Kubernetes Service i Azure Service Fabric, są najważniejsze części każdej istotnej mikrousług i aplikacji opartych na kontenerach. Aplikacje te mają wysoką złożoność, potrzeby skalowalności i przechodzą przez stałe ewolucje. W tym przewodniku wprowadzono koordynatorów i ich rolę w rozwiązaniach opartych na mikrousługach i kontenerach. Jeśli Twoja aplikacja jest przenoszona do bardziej złożonych aplikacji kontenerowych, warto zasięgnąć dodatkowych zasobów, aby dowiedzieć się więcej na temat programów Orchestrator.

>[!div class="step-by-step"]
>[Poprzednie](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
