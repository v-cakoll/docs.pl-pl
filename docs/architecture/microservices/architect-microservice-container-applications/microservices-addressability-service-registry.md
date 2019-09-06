---
title: Adresowanie mikrousług i rejestr usług
description: Zapoznaj się z rolą rejestrów obrazów kontenerów w architekturze mikrousług.
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295881"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresowanie mikrousług i rejestr usług

Każda mikrousługa ma unikatową nazwę (adres URL), która jest używana do rozpoznawania jego lokalizacji. Mikrousługa musi być adresowana wszędzie tam, gdzie jest uruchomiona. Jeśli chcesz się dowiedzieć, na którym komputerze działa dana mikrousługa, problemy mogą być szybko szybsze. W taki sam sposób, w jaki system DNS rozwiązuje adres URL określonego komputera, mikrousługa musi mieć unikatową nazwę, aby można było odnaleźć jej bieżącą lokalizację. Mikrousługi muszą mieć adresy nazw, które są niezależne od infrastruktury, w której są uruchomione. Oznacza to, że istnieje interakcja między wdrożeniem usługi a zakryciem, ponieważ istnieje konieczność korzystania z [rejestru usługi](https://microservices.io/patterns/service-registry.html). W tej samej przerostce, gdy komputer ulegnie awarii, usługa rejestru musi być w stanie wskazać, gdzie usługa jest teraz uruchomiona.

[Wzorzec rejestru usługi](https://microservices.io/patterns/service-registry.html) jest kluczowym elementem odnajdowania usług. Rejestr jest bazą danych zawierającą lokalizacje sieciowe wystąpień usługi. Rejestr usługi musi mieć wysoką dostępność i aktualność. Klienci mogą buforować lokalizacje sieciowe uzyskane z rejestru usługi. Jednak te informacje ostatecznie stają się nieaktualne, a klienci nie mogą odnajdywać wystąpień usługi. W związku z tym rejestr usługi składa się z klastra serwerów, które używają protokołu replikacji, aby zachować spójność.

W przypadku niektórych środowisk wdrażania mikrousług (nazywanych klastrami, które mają być objęte nowszą sekcją) Odnajdowanie usługi jest wbudowane. Na przykład środowisko Azure Container Service z Kubernetes (AKS) może obsłużyć rejestrację i Wyrejestrowanie wystąpienia usługi. Jest również uruchamiany serwer proxy na każdym hoście klastra, który odgrywa rolę routera odnajdywania po stronie serwera.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Krzysztof Richardson. Znaczne Rejestr usługi** \
  <https://microservices.io/patterns/service-registry.html>

- **Rozwiązanie Auth0. Rejestr usługi** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker. Odnajdowanie usług** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Poprzedni](maintain-microservice-apis.md)Następny
>[](microservice-based-composite-ui-shape-layout.md)
