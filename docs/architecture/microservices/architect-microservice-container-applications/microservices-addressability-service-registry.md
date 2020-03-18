---
title: Adresowanie mikrousług i rejestr usług
description: Zrozumienie roli rejestrów obrazów kontenerów w architekturze mikrousług.
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295881"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresowanie mikrousług i rejestr usług

Każda mikrousługa ma unikatową nazwę (URL), która jest używana do rozpoznawania jego lokalizacji. Mikrousługi muszą być adresowalne wszędzie tam, gdzie jest uruchomiona. Jeśli musisz pomyśleć o tym, który komputer jest uruchomiony określonej mikrousługi, rzeczy mogą iść źle szybko. W ten sam sposób, w jaki system DNS rozpoznaadres URL określonego komputera, mikrousługa musi mieć unikatową nazwę, aby jego bieżąca lokalizacja była wykrywalna. Mikrousługi wymagają adresowalnych nazw, które czynią je niezależnymi od infrastruktury, na której są uruchomione. Oznacza to, że istnieje interakcja między jak usługa jest wdrażana i jak jest wykrywany, ponieważ nie musi być [rejestr usługi](https://microservices.io/patterns/service-registry.html). W tym samym duchu, gdy komputer ulegnie awarii, usługa rejestru musi być w stanie wskazać, gdzie usługa jest teraz uruchomiona.

[Wzorzec rejestru usług](https://microservices.io/patterns/service-registry.html) jest kluczową częścią odnajdowania usługi. Rejestr jest bazą danych zawierającą lokalizacje sieciowe wystąpień usługi. Rejestr usług musi być wysoce dostępny i aktualny. Klienci mogą buforować lokalizacje sieciowe uzyskane z rejestru usługi. Jednak te informacje po pewnym czasie są nieaktualne, a klienci nie mogą już odnajdywać wystąpień usługi. W związku z tym rejestr usługi składa się z klastra serwerów, które używają protokołu replikacji w celu zachowania spójności.

W niektórych środowiskach wdrażania mikrousług (nazywanych klastrami, które mają być omówione w późniejszej sekcji), odnajdowanie usługi jest wbudowane. Na przykład usługa Azure Container Service ze środowiskiem Kubernetes (AKS) może obsługiwać rejestrację i wyrejestrowanie wystąpienia usługi. Uruchamia również serwer proxy na każdym hoście klastra, który odgrywa rolę routera odnajdowania po stronie serwera.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Chris Richardson. Wzorzec: Rejestr usługi** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0. Rejestr usług** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker. Odnajdowanie usługi** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Poprzedni](maintain-microservice-apis.md)
>[następny](microservice-based-composite-ui-shape-layout.md)
