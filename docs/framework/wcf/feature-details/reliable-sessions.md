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
ms.openlocfilehash: 396c76cbdb8eada881a5c87edfc2500dcdab3ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497168"
---
# <a name="reliable-sessions"></a>Niezawodne sesje

W tej sekcji opisano, jakie Windows Communication Foundation (WCF) niezawodna sesja jest, co umożliwia, jak i podczas użycia jednej, jakie konfiguracjami powiązań z jego obsługi oraz wskaźnikami na najlepszych rozwiązaniach dotyczących. W poniższej tabeli przedstawiono szczegółowe informacje o podstawowych punktów i Tematy pokrewne w tej sekcji.

Niezawodna sesja WCF zawiera featrues zapewnienie, że komunikaty wysyłane między punktami końcowymi są transferowane za pośrednictwem pośredników SOAP lub transportu i są dostarczane tylko raz i, opcjonalnie, w tej samej kolejności, w jakiej zostały wysłane.

Aby użyć niezawodnej sesji z aplikacją usługi WCF, użyj jednej z powiązania dostarczane przez system w programie WCF obsługujących niezawodnej sesji domyślnie lub opcjonalnie lub tworzenia własnego niestandardowego powiązania, który obsługuje sesji.

## <a name="in-this-section"></a>W tej sekcji

[Omówienie sesji niezawodnych](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
Opisuje niezawodnej sesji, kiedy należy używać ich różnych powiązań, które obsługuje niezawodnej sesji, i jak działają.

[Porady: wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
Opisuje sposób utworzenia niezawodnej sesji przez protokół HTTP przy użyciu niestandardowego powiązania określony w konfiguracji.

[Porady: Zabezpieczanie komunikatów w sesjach niezawodnych](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
Opis sposobu zabezpieczania niezawodnej sesji.

[Porady: tworzenie powiązania niestandardowego niezawodnej sesji z protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
Opisuje sposób utworzenia niezawodnej sesji przez protokół HTTPS.

[Najlepsze rozwiązania dotyczące sesji niezawodnych](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
Opis niektórych najlepszych praktyk związanych z użyciem niezawodnej sesji.

## <a name="reference"></a>Tematy pomocy

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Zobacz też

[Kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
[Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
