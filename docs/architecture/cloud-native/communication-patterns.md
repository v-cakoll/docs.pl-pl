---
title: Wzorce komunikacji rozwiązań natywnych dla chmury
description: Informacje o problemach z łącznością usług w aplikacjach natywnych w chmurze
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 3d678df44b5fef68427846e59f446b7408795625
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614217"
---
# <a name="cloud-native-communication-patterns"></a>Wzorce komunikacji rozwiązań natywnych dla chmury

Podczas konstruowania systemu natywnego w chmurze komunikacja jest istotną decyzją projektową. Jak aplikacja klienta frontonu komunikuje się z mikrousługą zaplecza? Jak usługa back-end komunikuje się ze sobą? Jakie są zasady, wzorce i najlepsze rozwiązania, które należy wziąć pod uwagę podczas implementowania komunikacji w aplikacjach natywnych w chmurze?

## <a name="communication-considerations"></a>Zagadnienia dotyczące komunikacji

W aplikacji monolitycznej komunikacja jest prosta. Moduły kodu są wykonywane razem w tym samym obszarze plików wykonywalnych (proces) na serwerze. Takie podejście może mieć zalety wydajności, ponieważ wszystkie elementy działają razem w pamięci współdzielonej, ale w przypadku ściśle sprzężonego kodu trudno zachować, rozwijać i skalować.

Systemy natywne w chmurze implementują architekturę opartą na mikrousługach z wieloma małymi, niezależnymi mikrousługami. Każda mikrousługa jest wykonywana w osobnym procesie i zazwyczaj jest uruchamiana wewnątrz kontenera wdrożonego w *klastrze*.

Klaster grupuje pulę maszyn wirtualnych w celu tworzenia środowiska o wysokiej dostępności. Są one zarządzane za pomocą narzędzia Orchestration, które jest odpowiedzialne za wdrażanie mikrousług kontenerów i zarządzanie nimi. Rysunek 4-1 przedstawia klaster [Kubernetes](https://kubernetes.io) wdrożony w chmurze platformy Azure z w pełni zarządzanymi [usługami Kubernetes platformy Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

![Klaster Kubernetes na platformie Azure](./media/kubernetes-cluster-in-azure.png)

**Rysunek 4-1**. Klaster Kubernetes na platformie Azure

W całym klastrze mikrousługi komunikują się ze sobą za pośrednictwem interfejsów API i technologii obsługi komunikatów.

Chociaż zapewniają wiele korzyści, mikrousługi nie są bezpłatnymi obiadami. Lokalne wywołania metod w procesie między składnikami są teraz zastępowane wywołaniami sieci. Każda mikrousługa musi komunikować się za pośrednictwem protokołu sieciowego, który dodaje złożoność do systemu:

- Przeciążenie sieci, opóźnienia i błędy przejściowe są stałą kwestią.

- Odporność (czyli ponawianie nieudanych żądań) jest istotna.

- Niektóre wywołania muszą być [idempotentne](https://www.restapitutorial.com/lessons/idempotency.html) , aby zachować spójny stan.

- Każda mikrousługa musi uwierzytelniać i autoryzować wywołania.

- Każdy komunikat musi być serializowany, a następnie deserializowany, co może być kosztowne.

- Szyfrowanie lub odszyfrowywanie wiadomości jest ważne.

Usługa Książka oparta na [platformie .NET: architektura dla kontenerów aplikacji platformy .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook), dostępna bezpłatnie od firmy Microsoft, zapewnia szczegółowe pokrycie wzorców komunikacji dla aplikacji mikrousług. W tym rozdziale udostępniamy ogólne omówienie tych wzorców wraz z opcjami implementacji dostępnymi w chmurze platformy Azure.

W tym rozdziale będziemy najpierw rozwiązywać komunikaty między aplikacjami frontonu a mikrousługami zaplecza. Następnie będziemy informować o mikrousługach zaplecza. Będziemy poznać technologię komunikacji w górę i w gRPC. Na koniec będziemy szukać nowych innowacyjnych wzorców komunikacji przy użyciu technologii siatki usług. Zobaczymy również, w jaki sposób usługa Azure Cloud oferuje różne rodzaje *usług zapasowych* w celu obsługi komunikacji natywnej w chmurze.

>[!div class="step-by-step"]
>[Poprzedni](other-deployment-options.md) 
> [Dalej](front-end-communication.md)
