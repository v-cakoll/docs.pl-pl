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
ms.openlocfilehash: 1d87f6f4d94763dc8f6ac7e929c22b17940097ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735428"
---
# <a name="reliable-sessions"></a>Niezawodne sesje

W tej sekcji opisano, jakie Windows Communication Foundation (WCF) jest niezawodnej sesji, jego przeznaczenie, jak i kiedy Aby użyć jednego, jakie konfiguracje powiązań z jego obsługi, a wskaźników na najlepsze rozwiązania. W poniższej tabeli przedstawiono szczegółowe informacje o podstawowych punktów i Tematy pokrewne w tej sekcji.

Sesja niezawodna WCF zapewnia featrues zagwarantowanie, że komunikaty wysyłane między punktami końcowymi są przenoszone między pośredników SOAP lub transportu i są dostarczane tylko raz i, opcjonalnie, w tej samej kolejności, w jakiej zostały wysłane.

Niezawodnej sesji za pomocą aplikacji WCF, użyj jednej z powiązań dostarczanych przez system w usłudze WCF, które obsługują niezawodnej sesji, domyślnie lub jako opcja lub utworzyć własne niestandardowe powiązanie, które obsługuje sesji.

## <a name="in-this-section"></a>W tej sekcji

[Omówienie sesji niezawodnych](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
W tym artykule opisano niezawodne sesje, kiedy należy używać ich różnych powiązań, które obsługuje sesji uwierzytelnianych i sposobie ich działania.

[Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
W tym artykule opisano sposób tworzenia niezawodnej sesji za pośrednictwem protokołu HTTP przy użyciu niestandardowego powiązania, określona w konfiguracji.

[Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
W tym artykule opisano, jak zabezpieczyć niezawodnej sesji.

[Instrukcje: Tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
W tym artykule opisano sposób tworzenia niezawodnej sesji za pośrednictwem protokołu HTTPS.

[Najlepsze rozwiązania dotyczące sesji niezawodnych](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
Opisuje niektóre najlepsze rozwiązania związane z używaniem niezawodnej sesji.

## <a name="reference"></a>Tematy pomocy

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Zobacz także

- [Kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
