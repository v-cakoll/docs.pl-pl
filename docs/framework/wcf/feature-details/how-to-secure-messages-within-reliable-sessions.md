---
title: 'Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 306d0f96b5163fe5c24d270b4b9a7c1d3f499e7e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596958"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych

W tym temacie opisano kroki wymagane do włączenia zabezpieczeń na poziomie komunikatów dla komunikatów wymienianych w ramach niezawodnej sesji przy użyciu jednego z powiązań dostarczonych przez system, które obsługują taką sesję, ale nie domyślnie. W razie potrzeby Włącz bezpieczną, niezawodną sesję przy użyciu kodu lub deklaratywnie w pliku konfiguracji. Ta procedura powoduje użycie plików konfiguracji klienta i usługi w celu włączenia bezpiecznej, niezawodnej sesji.

Ta procedura obejmuje następujące trzy kluczowe zadania:

1. Określ, że komunikaty programu Exchange klienta i usługi będą należeć do niezawodnej sesji.

1. Wymagaj zabezpieczeń na poziomie wiadomości w ramach niezawodnej sesji.

1. Określ typ poświadczeń klienta, który ma być używany przez klienta do uwierzytelniania w usłudze.

Ważne jest, aby najpierw wykonać pierwsze zadanie, że element konfiguracji punktu końcowego zawiera `bindingConfiguration` atrybut odwołujący się do konfiguracji powiązania o nazwie (w tym przykładzie) `MessageSecurity` . [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element Configuration następnie odwołuje się do tej nazwy, aby umożliwić niezawodne sesje przez ustawienie `enabled` atrybutu [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) elementu na `true` . Można wymagać, aby uporządkowane gwarancje dostarczania były dostępne w ramach niezawodnej sesji przez ustawienie `ordered` atrybutu na `true` .

Aby uzyskać kopię źródłową przykładowej procedury konfiguracji, zobacz [sesja niezawodna WS](../samples/ws-reliable-session.md).

Najważniejsze elementy drugiego zadania są wykonywane przez ustawienie `mode` atrybutu **\<security>** elementu zawartego w **\<binding>** elemencie klienta i usługi do `Message` .

Najważniejsze elementy trzeciego zadania są realizowane przez ustawienie `clientCredentialType` atrybutu **\<message>** elementu zawartego w **\<security>** elemencie klienta i usługi do `Certificate` .

> [!NOTE]
> W przypadku korzystania z zabezpieczeń komunikatów z niezawodnymi sesjami niezawodna komunikacja próbuje uwierzytelnić nieuwierzytelniony klient do momentu wystąpienia limitu czasu, zamiast zgłaszać wyjątek przy pierwszym błędzie.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie usługi za pomocą WSHttpBinding do korzystania z niezawodnej sesji

Ta procedura została opisana w artykule [How to: Exchange messages w niezawodnej sesji](how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie klienta z WSHttpBinding do korzystania z niezawodnej sesji

Ta procedura została opisana w artykule [How to: Exchange messages w niezawodnej sesji](how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Ustawianie trybu i wartości ClientCredentialtype w konfiguracji

1. Dodaj odpowiedni element powiązania do elementu w [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji. Poniższy przykład dodaje [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.

1. Dodaj **\<binding>** element i ustaw jego `name` atrybut na odpowiednią wartość. W przykładzie używa się nazwy `MessageSecurity` .

1. Dodaj **\<security>** element i ustaw `mode` atrybut na `Message` .

1. W **\<security>** elemencie Dodaj **\<message>** element i ustaw `clientCredentialType` atrybut na `Certificate` .

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
