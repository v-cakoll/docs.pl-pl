---
title: Zabezpieczenia w aplikacjach gRPC - gRPC dla programistów WCF
description: Omówienie uwierzytelniania i autoryzacji połączeń i kanałów w gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147818"
---
# <a name="security-in-grpc-applications"></a>Zabezpieczenia w aplikacjach gRPC

W każdym scenariuszu rzeczywistym zabezpieczenie aplikacji i usług jest niezbędne. Zabezpieczenia obejmują trzy kluczowe obszary:

* Szyfrowanie ruchu sieciowego w celu uniemożliwienia przechwyceniu go przez złośliwych hakerów.
* Uwierzytelnianie klientów i serwerów w celu ustalenia tożsamości i zaufania.
* Autoryzowanie klientów do kontrolowania dostępu do systemów i stosowania uprawnień na podstawie tożsamości.

> [!NOTE]
> *Uwierzytelnianie* dotyczy ustalenia tożsamości klienta lub serwera. *Autoryzacja* dotyczy określenia, czy klient ma uprawnienia dostępu do zasobu lub wydania polecenia.

Niniejszy rozdział obejmie udogodnienia uwierzytelniania i autoryzacji w gRPC dla ASP.NET Core. Omówi również zabezpieczenia sieci za pośrednictwem szyfrowanych połączeń TLS.

## <a name="wcf-authentication-and-authorization"></a>Uwierzytelnianie i autoryzacja WCF

W programie Windows Communication Foundation (WCF) uwierzytelnianie i autoryzacja były obsługiwane na różne sposoby, w zależności od używanych transportów i powiązań. WCF obsługiwane różne Standardy\* zabezpieczeń WS. Obsługa uwierzytelniania systemu Windows dla usług HTTP działających w usługach IIS lub NetTCP między systemami Windows.

## <a name="grpc-authentication-and-authorization"></a>uwierzytelnianie i autoryzacja gRPC

Uwierzytelnianie i autoryzacja gRPC działa na dwóch poziomach:

* Uwierzytelnianie/autoryzacja na poziomie wywołania jest zwykle obsługiwane za pomocą tokenów, które są stosowane w metadanych po nadaniu wywołania.
* Uwierzytelnianie na poziomie kanału używa certyfikatu klienta, który jest stosowany na poziomie połączenia. Może również zawierać poświadczenia uwierzytelniania/autoryzacji na poziomie wywołania, które mają być stosowane do każdego wywołania na kanale automatycznie.

Można użyć jednego lub obu tych mechanizmów, aby pomóc zabezpieczyć usługę.

Implementacja ASP.NET Core gRPC obsługuje uwierzytelnianie i autoryzację za pośrednictwem większości standardowych mechanizmów ASP.NET Core:

- Uwierzytelnianie połączeń
  - Usługa Azure Active Directory
  - Serwer tożsamości
  - Token nośny JWT
  - OAuth 2.0
  - OpenID Connect
  - WS-Federation
- Uwierzytelnianie kanału
  - Certyfikat klienta

Wszystkie metody uwierzytelniania wywołań są oparte na *tokenach*. Jedyną rzeczywistą różnicą jest sposób generowania tokenów i bibliotek, które są używane do sprawdzania poprawności tokenów w usłudze ASP.NET Core.

Aby uzyskać więcej informacji, zobacz [artykuł Uwierzytelnianie i autoryzacja.](/aspnet/core/grpc/authn-and-authz)

> [!NOTE]
> Jeśli używasz gRPC za pośrednictwem szyfrowanego tls połączenia HTTP/2, cały ruch między klientami i serwerami jest szyfrowany, nawet jeśli nie używasz uwierzytelniania na poziomie kanału.

W tym rozdziale pokaże, jak zastosować poświadczenia wywołania i poświadczenia kanału do usługi gRPC. Pokaże również, jak używać poświadczeń z klienta gRPC .NET Core do uwierzytelniania z usługą.

>[!div class="step-by-step"]
>[Poprzedni](client-libraries.md)
>[następny](call-credentials.md)
