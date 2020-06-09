---
title: Niezawodne sesje
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590543"
---
# <a name="reliable-sessions"></a>Niezawodne sesje

W tej sekcji opisano, co to jest Niezawodna sesja programu Windows Communication Foundation (WCF), co jest używane przez program, jak i kiedy należy z nich korzystać, jakie konfiguracje powiązań obsługują i jakie są wskaźniki najlepszych rozwiązań. Poniższa tabela zawiera podsumowanie szczegółowych informacji o najważniejszych punktach i powiązanych tematach w tej sekcji.

Funkcja WCF dla niezawodnej sesji zapewnia funkcje zapewniające, że komunikaty wysyłane między punktami końcowymi są przesyłane przez wystawcy protokołu SOAP lub transportu i są dostarczane tylko raz i, opcjonalnie, w takiej samej kolejności, w jakiej zostały wysłane.

Aby używać niezawodnej sesji z aplikacją WCF, użyj jednego z powiązań dostarczonych przez system w programie WCF, który domyślnie obsługuje niezawodną sesję lub jako opcję, lub Utwórz własne niestandardowe powiązanie, które obsługuje daną sesję.

## <a name="in-this-section"></a>W tej sekcji

[Omówienie sesji niezawodnych](reliable-sessions-overview.md) Opisuje niezawodne sesje, gdy ich używać, różne powiązania, które obsługują niezawodne sesje i jak działają.

[Instrukcje: Wymiana komunikatów w ramach niezawodnej sesji](how-to-exchange-messages-within-a-reliable-session.md) Opisuje sposób tworzenia niezawodnej sesji za pośrednictwem protokołu HTTP przy użyciu niestandardowego powiązania określonego w konfiguracji.

[Instrukcje: Zabezpieczanie komunikatów w ramach sesji niezawodnych](how-to-secure-messages-within-reliable-sessions.md) Opisuje sposób zabezpieczania niezawodnej sesji.

[Instrukcje: Tworzenie niestandardowego powiązania niezawodnej sesji z protokołem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Opisuje sposób tworzenia niezawodnej sesji za pośrednictwem protokołu HTTPS.

[Najlepsze rozwiązania dotyczące niezawodnych sesji](best-practices-for-reliable-sessions.md) W tym artykule opisano niektóre najlepsze rozwiązania związane z używaniem niezawodnej sesji.

## <a name="reference"></a>Dokumentacja

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Zobacz też

- [Kolejki i sesje niezawodne](queues-and-reliable-sessions.md)
- [Sesje, tworzenie wystąpień i współbieżność](sessions-instancing-and-concurrency.md)
