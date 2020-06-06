---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139664"
---
# \<bindings>

Można użyć elementu, `bindings` Aby skonfigurować kolekcję powiązań standardowych i niestandardowych dla Windows Communication Foundation (WCF). Każdy wpis jest `binding` elementem, który może być identyfikowany przez jego unikatowy `name` . Usługi używają powiązań przez łączenie ich przy użyciu `name` . Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="system-provided-bindings"></a>Powiązania dostarczone przez system

Powiązania dostarczane przez system ukrywają złożoność stosu komunikatów WCF. Aplikacje korzystające z powiązań dostarczonych przez system nie wymagają pełnej kontroli nad stosem. Atrybuty uwidocznione dla każdego powiązania dostarczonego przez system są najbardziej odpowiednie dla scenariusza użycia.

Sekcja konfiguracji dla każdego powiązania dostarczonego przez system może definiować kilka konfiguracji używanych do konfigurowania powiązania. Każda konfiguracja jest identyfikowana przy użyciu unikatowej nazwy.

Nie jest możliwe dodawanie elementów lub atrybutów do powiązania dostarczonego przez system. Aby to zrobić, należy zaimplementować niestandardowe powiązanie zgodnie z opisem w sekcji [powiązania niestandardowe](#custom-bindings) . Istnieje możliwość zdefiniowania niestandardowego powiązania, które naśladuje powiązanie dostarczone przez system i dodaje kilka ustawień, które aplikacja użytkownika chce mieć kontrolę.  

Aby uzyskać listę powiązań dostarczanych przez system, zobacz [powiązania dostarczone przez system](../../../wcf/system-provided-bindings.md).

## <a name="custom-bindings"></a>Powiązania niestandardowe

Niestandardowe powiązania zapewniają pełną kontrolę nad stosem obsługi komunikatów WCF. Pojedyncze powiązanie definiuje stos komunikatów przez określenie elementów konfiguracji dla elementów stosu w kolejności, w jakiej występują na stosie. Każdy element definiuje i konfiguruje jeden element stosu. Musi istnieć jeden i tylko jeden `transport` element w każdym powiązaniu niestandardowym. Bez tego elementu stos komunikatów jest niekompletny.

Kolejność, w której elementy pojawiają się w kwestiach stosu, ponieważ jest to kolejność, w której operacje są stosowane do wiadomości. Wymagana kolejność elementów stosu jest następująca:  

1. Transakcje (opcjonalnie)  

2. Niezawodna obsługa komunikatów (opcjonalnie)  

3. Zabezpieczenia (opcjonalnie)  

4. Pomocą  

5. Transport  

 Niestandardowe powiązania są identyfikowane przez ich `name` atrybut. Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [niestandardowe powiązania](../../../wcf/extending/custom-bindings.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [Powiązania](../../../wcf/bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
