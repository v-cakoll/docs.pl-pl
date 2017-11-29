---
title: takeaways klucza
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | takeaways klucza"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b557d0b641bfe95c025cadb13f82c3f8927f4bc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="key-takeaways"></a>Takeaways klucza

Podsumowanie i takeaways klucza poniżej przedstawiono najważniejsze wnioski z tego przewodnika.

**Zalety używania kontenerów.** Rozwiązań kontenera Podaj istotne korzyści wynikające z oszczędności, ponieważ kontenerów do rozwiązania problemów z wdrażaniem spowodowane brakiem zależności w środowiskach produkcyjnych. Kontenery znacznie zwiększyć operacje DevOps i produkcji.

**Kontenery będzie uniwersalnych.** Na podstawie docker kontenery stają się coraz faktyczne standardowego w branży kontenera, obsługiwanych przez dostawców najbardziej znaczących w ekosystemami systemu Windows i Linux. W tym firmy Microsoft, Amazon AWS Google i IBM. W niedalekiej przyszłości Docker prawdopodobnie będzie wszechobecne w chmurze, jak i dla lokalnego centrach danych.

**Kontenery jako część wdrożenia.** Kontener Docker staje się coraz standardowe jednostki wdrożenia żadnych usług ani aplikacji serwerowych.

**Mikrousług.** Architektura mikrousług staje się coraz preferowane podejście do rozproszonego i dużych lub złożonych kluczowych aplikacji oparte na wiele niezależnych podsystemów w formie autonomicznej usług. W architektura mikrousługi aplikacji jest utworzony jako kolekcję usług, które mogą być rozwinięte, przetestowane, wersji, wdrożyć i skalowane niezależnie; może to obejmować wszystkie powiązane autonomicznej bazy danych.

**Projektowanie oparte na domenie i SOA.** Wzorce architektura mikrousług pochodzić od zorientowane na usługę architektury (SOA) i opartych na domenie projektu (DDD). Podczas projektowania i opracowywania mikrousług dla środowisk ze zmianami reguł biznesowych, kształtowania konkretnej domeny, ważne jest uwzględnienie podejścia DDD konta i wzorce.

**Wyzwania Mikrousług.** Mikrousług oferują wiele funkcji zaawansowanych, takich jak niezależnie od wdrażania, silne podsystemu granice i różnorodność technologii. Jednak ich też wiązać się z wielu wyzwania związane z projektowanie aplikacji rozproszonych, takich jak fragmentacji i modeli danych niezależnych, odporne komunikację między mikrousług, spójność ostateczna i złożoność działania, będącą wynikiem agregowanie informacji logowania i monitorowania z wielu mikrousług. Te aspekty wprowadzenie wyższy poziom złożoności niż tradycyjne aplikacja wbudowanymi. W związku z tym tylko określonych scenariuszy nadają się do aplikacji opartych na mikrousługi. Obejmują one aplikacje dużych i złożonych z wielu podsystemami zmieniające się; w takich przypadkach warto zainwestować w bardziej złożonych architektura oprogramowania, ponieważ będzie on zawierał lepiej długoterminowej elastyczność i konserwacja aplikacji.

**Kontenery dla dowolnej aplikacji.** Kontenery jest wygodną metodą mikrousług, ale nie są wyłączne dla nich. Można także kontenery z wbudowanymi aplikacjami, w tym starsze aplikacje oparte na tradycyjnych .NET Framework i modernizowana za pośrednictwem kontenery systemu Windows. Korzyści wynikające ze stosowania Docker, takie jak rozwiązywanie wielu problemów wdrożenia do produkcji i udostępnia najnowocześniejsze środowiskach programistycznych i testowych, mają zastosowanie do wielu różnych typów aplikacji.

**Interfejs wiersza polecenia i IDE.** Narzędzia Microsoft można programować konteneryzowanych aplikacji .NET przy użyciu Twojej preferowane rozwiązanie. Można programować za pomocą interfejsu wiersza polecenia i środowisk Edytor przy użyciu interfejsu wiersza polecenia Docker i Visual Studio Code. Lub można używać podejście fokus IDE programu Visual Studio i jego funkcje unikatowy dla Docker, takie jak możliwość debugowania aplikacji usługi kontenera.

**Aplikacje w chmurze odporność.** W systemach rozproszonych i systemów opartych na chmurze ogólnie rzecz biorąc, jest zawsze ryzyko wystąpienia awarii częściowej. Ponieważ klienci i usługi są osobne procesy (kontenery), usługa nie może być stanie odpowiedzieć w odpowiednim momencie na żądanie klienta. Na przykład usługa może być wyłączony z powodu błędu częściowego lub obsługi; Usługa może być przeciążona i odpowiada bardzo wolno do żądań; lub może po prostu nie być dostępne przez krótki czas z powodu problemów dotyczących sieci. W związku z tym aplikacją opartą na chmurze musi obejmować te błędy i mieć strategii w miejscu, aby odpowiedzieć na te błędy. Strategie te mogą obejmować zasady ponawiania (ponowne wysyłanie wiadomości lub ponawianie żądań) i implementujący wzorce wyłącznika — Aby uniknąć wykładniczej obciążenia żądań powtórzony. Zasadniczo aplikacji opartych na chmurze muszą mieć odporność mechanizmów — niestandardowe tych albo takich, które jest oparte na infrastrukturze chmury, takich jak wysokiego poziomu struktury z orchestrators lub magistrali usługi.

**Zabezpieczenia.** Nasze współczesnym świecie kontenerów i mikrousług mogą uwidaczniać nowych luk w zabezpieczeniach. Podstawowych zabezpieczeniach aplikacji na podstawie uwierzytelniania i autoryzacji; istnieje wiele sposobów te implementacji. Jednak kontenera zabezpieczeń obejmuje dodatkowe najważniejsze składniki wynikających z założenia bezpieczniejsze aplikacji. Najważniejszym elementem tworzenia aplikacji bezpieczniejsze jest problem bezpieczny sposób komunikowania się z innych aplikacji i systemów, coś to często wymaga poświadczeń, tokeny, hasła i inne poufne informacje — zwykle określonych jako klucze tajne aplikacji. Żadne rozwiązanie do bezpiecznego wykonaj najlepsze rozwiązania w zakresie zabezpieczeń, na przykład szyfrowanie kluczy tajnych przesyłanych; szyfrowanie kluczy tajnych magazynowane; i uniemożliwia przypadkowo przeciek, gdy używane przez aplikację końcowego kluczy tajnych. Te klucze tajne muszą być przechowywane i były bezpieczne, umieszczone w innym miejscu. Aby ułatwić z zabezpieczeniami, możesz korzystać infrastruktury orchestrator wybrany lub infrastruktury chmury, takich jak usługi Azure Key Vault i sposoby zapewnia kod aplikacji w celu używania go.

**Orchestrators.** Na podstawie kontenera orchestrators, takich jak te dostępne w usłudze kontenera platformy Azure (Kubernetes Mesos DC/OS i Docker Swarm) i sieci szkieletowej usług Azure są niezbędne dla każdej aplikacji na podstawie mikrousługi gotowe do produkcji, jak i dla dowolnej usługi kontenera Aplikacja o znaczących złożoności, skalowalność potrzeb i rozwoju stałej. W tym przewodniku została wprowadzona orchestrators i ich roli w rozwiązaniach mikrousługi, jak i na podstawie kontenera. Jeśli do potrzeb aplikacji przenosisz kierunku złożonych aplikacji konteneryzowanych, znajduje się on przydatne do poszukiwania dodatkowe zasoby, aby uzyskać więcej informacji na temat orchestrators

>[!div class="step-by-step"]
[Poprzednie] (secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
