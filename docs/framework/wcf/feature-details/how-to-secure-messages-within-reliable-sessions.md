---
title: 'Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
author: BrucePerlerMS
ms.openlocfilehash: f3269dc96dee2d534a8dd6677abeb6afae8776bd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196723"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych

W tym temacie opisano kroki wymagane w celu umożliwienia zabezpieczenia na poziomie komunikatu dla komunikatów wymienianych w ramach niezawodnej sesji przy użyciu jednej z powiązań dostarczanych przez system, które obsługują sesji programu, ale nie domyślnie. Włącz bezpieczne i niezawodne sesji obowiązkowo przy użyciu kodu lub deklaratywnie w pliku konfiguracji. Ta procedura używa plików konfiguracji klienta i usługi, aby umożliwić bezpieczne i niezawodne sesji.

Ta procedura obejmuje następujące trzy kluczowe zadania:

1. Określ, czy klient i usługa wymiana komunikatów w ramach niezawodnej sesji.

1. Wymagaj zabezpieczenia na poziomie komunikatu w ramach niezawodnej sesji.

1. Określanie typu poświadczeń klienta, który klient musi używać uwierzytelniania za pomocą usługi.

Jest ważne w pierwszym zadaniu, który zawiera element konfiguracji punktu końcowego `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie (w tym przykładzie) `MessageSecurity`. [  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się następnie tę nazwę, aby włączyć niezawodnej sesji przez ustawienie `enabled` atrybutu [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elementu `true`. Możesz wymagać, że gwarancje dostarczenia uporządkowane są dostępne w ramach sesji niezawodnej, ustawiając `ordered` atrybutu `true`.

Dla źródła kopii przykładu, na którym opiera się poniższą procedurę konfiguracji, zobacz [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Podstawowe elementy drugie zadanie podrzędne są realizowane przez ustawienie `mode` atrybutu  **\<zabezpieczeń >** elementów znajdujących się w  **\<powiązania >** Element klienta i usługi w celu `Message`.

Podstawowe elementy trzeci zadania są wykonywane przez ustawienie `clientCredentialType` atrybutu  **\<komunikatu >** elementów znajdujących się w  **\<zabezpieczeń >** Element klienta i usługi w celu `Certificate`.

> [!NOTE]
> Korzystanie z zabezpieczeń komunikatów za pomocą sesji niezawodnych, niezawodną obsługę komunikatów próbuje uwierzytelnić klienta nieuwierzytelnione, dopóki nie zostanie przekroczony limit czasu zamiast zgłaszać wyjątek po pierwszym niepowodzeniu.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie usługi przy użyciu WSHttpBinding używać niezawodnej sesji

Ta procedura jest opisana w [instrukcje: wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie klienta za pomocą WSHttpBinding używać niezawodnej sesji

Ta procedura jest opisana w [instrukcje: wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Ustaw tryb i właściwości ClientCredentialType o wartości w konfiguracji

1. Dodaj odpowiednie powiązanie elementu [  **\<powiązania >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element pliku konfiguracji. W poniższym przykładzie dodano [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.

1. Dodaj  **\<powiązania >** element i ustaw jego `name` atrybutu do odpowiedniej wartości. W przykładzie użyto nazwy `MessageSecurity`.

1. Dodaj  **\<zabezpieczeń >** element i ustaw `mode` atrybutu `Message`.

1. W ramach  **\<zabezpieczeń >** elementu Dodawanie  **\<komunikat >** element i ustaw `clientCredentialType` atrybutu `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
