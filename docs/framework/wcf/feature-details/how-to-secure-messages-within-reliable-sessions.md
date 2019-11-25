---
title: 'Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: edff27fe9649387c1922c34e72ef59d615e52b90
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141664"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych

W tym temacie opisano kroki wymagane do włączenia zabezpieczeń na poziomie komunikatów dla komunikatów wymienianych w ramach niezawodnej sesji przy użyciu jednego z powiązań dostarczonych przez system, które obsługują taką sesję, ale nie domyślnie. W razie potrzeby Włącz bezpieczną, niezawodną sesję przy użyciu kodu lub deklaratywnie w pliku konfiguracji. Ta procedura powoduje użycie plików konfiguracji klienta i usługi w celu włączenia bezpiecznej, niezawodnej sesji.

Ta procedura obejmuje następujące trzy kluczowe zadania:

1. Określ, że komunikaty programu Exchange klienta i usługi będą należeć do niezawodnej sesji.

1. Wymagaj zabezpieczeń na poziomie wiadomości w ramach niezawodnej sesji.

1. Określ typ poświadczeń klienta, który ma być używany przez klienta do uwierzytelniania w usłudze.

Ważne jest, aby najpierw wykonać pierwsze zadanie, że element konfiguracji punktu końcowego zawiera atrybut `bindingConfiguration`, który odwołuje się do konfiguracji powiązania o nazwie (w tym przykładzie) `MessageSecurity`. Element konfiguracji [ **> powiązania\<** ](../../configure-apps/file-schema/wcf/bindings.md) następnie odwołuje się do tej nazwy w celu włączenia niezawodnych sesji przez ustawienie atrybutu `enabled` elementu [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) w `true`. Można wymagać, aby w ramach niezawodnej sesji były dostępne uporządkowane gwarancje dostarczania, ustawiając atrybut `ordered` na `true`.

Aby uzyskać kopię źródłową przykładowej procedury konfiguracji, zobacz [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Najważniejsze elementy drugiego zadania są wykonywane przez ustawienie atrybutu `mode` elementu **\<security >** zawartych w elemencie **\<Binding >** klienta i usługi do `Message`.

Najważniejsze elementy trzeciego zadania są realizowane przez ustawienie atrybutu `clientCredentialType` **komunikatu\<** elementu zawartego w elemencie **\<Security >** klienta i usługi do `Certificate`.

> [!NOTE]
> W przypadku korzystania z zabezpieczeń komunikatów z niezawodnymi sesjami niezawodna komunikacja próbuje uwierzytelnić nieuwierzytelniony klient do momentu wystąpienia limitu czasu, zamiast zgłaszać wyjątek przy pierwszym błędzie.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie usługi za pomocą WSHttpBinding do korzystania z niezawodnej sesji

Ta procedura została opisana w artykule [How to: Exchange messages w niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie klienta z WSHttpBinding do korzystania z niezawodnej sesji

Ta procedura została opisana w artykule [How to: Exchange messages w niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Ustawianie trybu i wartości ClientCredentialtype w konfiguracji

1. Dodaj odpowiedni element powiązania do elementu [ **\<powiązania >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji. Poniższy przykład dodaje element [ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .

1. Dodaj element **> powiązania\<** i ustaw jego atrybut `name` na odpowiednią wartość. W przykładzie użyta jest nazwa `MessageSecurity`.

1. Dodaj element **\<security >** i ustaw atrybut `mode` na `Message`.

1. W elemencie **\<security >** dodaj element **\<Message >** i ustaw atrybut `clientCredentialType` na `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
