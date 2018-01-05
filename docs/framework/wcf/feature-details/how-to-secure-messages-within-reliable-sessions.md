---
title: "Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 254cc241edf2d1c53ce9dd14eee41cd8bf6eaa76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych

W tym temacie opisano kroki wymagane do włączenia zabezpieczenia na poziomie komunikatu dla komunikatów wymieniane w niezawodnej sesji przy użyciu jednej powiązań dostarczane przez system, które obsługują sesji programu, ale nie domyślnie. Włącz sesji bezpieczne, niezawodne imperatively przy użyciu kodu lub deklaratywnie w pliku konfiguracji. Ta procedura wykorzystuje pliki konfiguracji klienta i usługi umożliwia bezpieczne, niezawodne sesji.

Ta procedura składa się z trzech poniższych zadań głównych:

1. Określ, czy klient i usługa wymiana komunikatów w ramach niezawodnej sesji.

1. Wymagaj zabezpieczenia na poziomie komunikatu niezawodnej sesji.

1. Określ typ poświadczeń klienta, które klient musi używać uwierzytelniania za pomocą usługi.

Jest ważne w pierwszym zadaniu, który zawiera element konfiguracji punktu końcowego `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie (w tym przykładzie) `MessageSecurity`. [  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się następnie tę nazwę, aby włączyć niezawodnej sesji przez ustawienie `enabled` atrybutu [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elementu `true`. Można wymagać, aby gwarancje uporządkowanego dostarczenia są dostępne w ramach niezawodnej sesji przez ustawienie `ordered` atrybutu `true`.

Źródło kopii przykładu, na której oparto tej procedury konfiguracji, zobacz [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Podstawowych elementów drugiego zadania są realizowane przez ustawienie `mode` atrybutu  **\<zabezpieczeń >** element zawarty w  **\<powiązania >** Element klienta i usługi `Message`.

Podstawowych elementów trzeci zadań są realizowane przez ustawienie `clientCredentialType` atrybutu  **\<wiadomości >** element zawarty w  **\<zabezpieczeń >** Element klienta i usługi `Certificate`.

> [!NOTE]
> Jeśli zabezpieczenia komunikatów z sesji niezawodnych, niezawodna obsługa komunikatów podejmuje próbę uwierzytelnienia klienta nieuwierzytelnione, dopóki nie zostanie przekroczony limit czasu zamiast generowania wyjątku przy pierwszym niepowodzeniu.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Skonfiguruj usługę z WSHttpBinding do użycia niezawodnej sesji

Ta procedura jest opisana w [porady: wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie klienta z WSHttpBinding do użycia niezawodnej sesji

Ta procedura jest opisana w [porady: wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Ustaw tryb i ClientCredentialType w konfiguracji

1. Dodaj odpowiednie powiązanie elementu [  **\<powiązania >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu w pliku konfiguracji. W poniższym przykładzie dodano [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.

1. Dodaj  **\<powiązania >** element i ustaw jej `name` atrybutu odpowiednią wartość. W przykładzie użyto nazwy `MessageSecurity`.

1. Dodaj  **\<zabezpieczeń >** element i ustaw `mode` atrybutu `Message`.

1. W ramach  **\<zabezpieczeń >** elementu, Dodaj  **\<wiadomości >** element i ustaw `clientCredentialType` atrybutu `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
