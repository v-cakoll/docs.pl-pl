---
title: Omówienie gRPC-gRPC dla deweloperów programu WCF
description: Dowiedz się więcej na temat zestawu zasad dotyczących opracowywania gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: a0811adadc617097d86edc5f845c42a7e90f560f
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542926"
---
# <a name="grpc-overview"></a>gRPC — Omówienie

Po przejrzeniu Genesis obu Windows Communication Foundation (WCF) i gRPC w ostatnim rozdziale ten rozdział uwzględnia niektóre kluczowe funkcje gRPC i sposób ich porównywania z usługą WCF.

ASP.NET Core 3,0 to pierwsza wersja ASP.NET, która natywnie obsługuje gRPC jako obywatel pierwszej klasy, a firma Microsoft Teams uczestniczy w oficjalnej implementacji platformy .NET gRPC. Jest to zalecane w przypadku kompilowania aplikacji rozproszonych za pomocą platformy .NET, które mogą współdziałać ze wszystkimi innymi głównymi językami programowania i strukturami.

## <a name="key-principles"></a>Najważniejsze zasady

Zgodnie z opisem w rozdziale 1 Firma Google chciała wykorzystać wprowadzenie protokołu HTTP/2 do zastępowania stubby, jego wewnętrznej infrastruktury usługi RPC ogólnego przeznaczenia. gRPC, w oparciu o stubby, może korzystać z standaryzacji i spowodować, że będzie to miało zastosowanie do rozwiązań mobilnych, chmur i Internet rzeczy.

Aby to osiągnąć, w [chmurze Native Computing Foundation (CNCF)](https://www.cncf.io/) ustanowiono zestaw zasad, które mogłyby zarządzać gRPC. Na poniższej liście przedstawiono najbardziej odpowiednie, te, które zostały głównie objęte maksymalizacją dostępności i użyteczność:

- **Bezpłatna i otwarta** — wszystkie artefakty powinny być otwarte w ramach licencjonowania, które nie ograniczają deweloperom przyjmowania gRPC.
- **Zakres i prostota** — gRPC powinna być dostępna dla każdej popularnej platformy i jest wystarczająco prosta do kompilowania na dowolnej platformie.
- **Współdziałanie i zasięg** — powinno być możliwe użycie gRPC w dowolnej sieci, niezależnie od przepustowości lub opóźnienia, przy użyciu powszechnie dostępnych standardów sieci.
- **Ogólnego przeznaczenia i wykonywania** — platforma powinna być użyteczna w szerokim zakresie przypadków użycia, bez obniżania wydajności.
- **Przesyłanie strumieniowe** — protokół powinien udostępniać semantykę przesyłania strumieniowego dla dużych zestawów danych lub asynchronicznej obsługi komunikatów.
- **Wymiana metadanych** — protokół umożliwia obsługę danych nienależących do firmy, takich jak tokeny uwierzytelniania, niezależnie od rzeczywistych danych firmy.
- **Standardowe kody stanu** — zmienność kodów błędów powinna zostać zmniejszona, aby umożliwić bardziej przejrzyste podejmowanie decyzji dotyczących obsługi błędów. Gdy wymagana jest dodatkowa, bogatsza obsługa błędów, należy zapewnić mechanizm zarządzania w ramach wymiany metadanych.

>[!div class="step-by-step"]
>[Poprzednie](introduction.md)
>[dalej](approach.md)
