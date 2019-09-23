---
title: Omówienie gRPC-gRPC dla deweloperów programu WCF
description: Dowiedz się więcej na temat zestawu zasad dotyczących opracowywania gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b372cc9dcdb2efd605b3d9b688513e4ff8530b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184443"
---
# <a name="grpc-overview"></a>gRPC — Omówienie

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Po przejrzeniu Genesis zarówno programu WCF, jak i gRPC w ostatnim rozdziale, ten rozdział będzie uwzględniać niektóre kluczowe funkcje gRPC i porównać je z programem WCF.

ASP.NET Core 3,0 to pierwsza wersja ASP.NET, która natywnie obsługuje gRPC jako obywatel pierwszej klasy, a firma Microsoft Teams uczestniczy w oficjalnej implementacji platformy .NET gRPC. Zaleca się, aby najlepszym podejściem do kompilowania aplikacji rozproszonych za pomocą platformy .NET było współdziałanie ze wszystkimi innymi głównymi językami programowania i strukturami.

## <a name="key-principles"></a>Podstawowe zasady

Jak zostało to omówione w rozdziale 1, firma Google chciała wykorzystać wprowadzenie protokołu HTTP/2 do współdziałania stubby, jego wewnętrznej infrastruktury usługi RPC ogólnego przeznaczenia. Stubby, zmieniono nazwę gRPC, teraz może wykorzystać standaryzację i spowodować jej zastosowanie do przetwarzania przenośnego, chmury i Internet rzeczy.

Aby to osiągnąć, w [chmurze Native Computing Foundation (CNCF)](https://www.cncf.io/) ustanowiono zestaw zasad, które mogłyby zarządzać gRPC. Na poniższej liście przedstawiono najbardziej odpowiednie, te, które zostały głównie objęte maksymalizacją dostępności i użyteczność:

- **Bezpłatna i otwarta** — wszystkie artefakty powinny być otwarte w ramach licencjonowania, które nie ograniczają deweloperom przyjmowania gRPC.
- **Zakres i prostota** — gRPC powinna być dostępna dla każdej popularnej platformy i jest wystarczająco prosta do kompilowania na dowolnej platformie.
- **Współdziałanie i zasięg** — powinno być możliwe korzystanie z gRPC w dowolnej sieci, niezależnie od przepustowości lub opóźnienia, przy użyciu powszechnie dostępnych standardów sieci.
- **Ogólnego przeznaczenia i wykonywania** — struktura powinna być użyteczna w szerokim zakresie przypadków użycia bez kompromisu wydajności.
- **Przesyłanie strumieniowe** — protokół powinien udostępniać semantykę przesyłania strumieniowego dla dużych zestawów danych lub asynchronicznej obsługi komunikatów.
- **Wymiana metadanych** — protokół zezwala na obsługę danych nienależących do firmy, takich jak tokeny uwierzytelniania, niezależnie od rzeczywistych danych firmy.
- **Standardowe kody Stanów** — zmienność kodów błędów powinna być zredukowana, aby umożliwić bardziej przejrzyste podejmowanie decyzji o obsłudze błędów oraz, gdy wymagana jest dodatkowa obsługa błędów, należy zapewnić mechanizm zarządzania w ramach wymiany metadanych.

>[!div class="step-by-step"]
>[Poprzedni](introduction.md)
>[Następny](approach.md)
