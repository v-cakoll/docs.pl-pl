---
title: Zabezpieczenia w aplikacjach gRPC — gRPC dla deweloperów WCF
description: Omówienie uwierzytelniania wywołań i kanałów oraz autoryzacji w programie gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: d5804ad5de4a834eb81b90fa1ea7a61969a0b42f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503409"
---
# <a name="security-in-grpc-applications"></a>Zabezpieczenia w aplikacjach gRPC

W dowolnym rzeczywistym scenariuszu Zabezpieczanie aplikacji i usług jest niezbędne. Zabezpieczenia obejmują trzy kluczowe obszary: 

* Szyfrowanie ruchu sieciowego, aby zapobiec przechwyceniu go przez złośliwych hakerów.
* Uwierzytelnianie klientów i serwerów w celu ustanowienia tożsamości i zaufania.
* Autoryzowanie klientów do kontrolowania dostępu do systemów i stosowania uprawnień na podstawie tożsamości.

> [!NOTE]
> *Uwierzytelnianie* dotyczy ustanowienia tożsamości klienta lub serwera. *Autoryzacja* jest zaangażowana w ustalanie, czy klient ma uprawnienia dostępu do zasobu, czy wydać polecenie.

Ten rozdział obejmuje funkcje uwierzytelniania i autoryzacji w programie gRPC dla ASP.NET Core. Będzie również omawiać zabezpieczenia sieci przy użyciu szyfrowanych połączeń TLS.

## <a name="wcf-authentication-and-authorization"></a>Uwierzytelnianie i autoryzacja w programie WCF

W programie Windows Communication Foundation (WCF) uwierzytelnianie i autoryzacja zostały obsłużone na różne sposoby, w zależności od używanych transportów i powiązań. Obsługiwane są różne standardy zabezpieczeń WS-\* WCF. Obsługiwane jest również uwierzytelnianie systemu Windows dla usług HTTP uruchomionych w usługach IIS lub NetTCP Services między systemami Windows.

## <a name="grpc-authentication-and-authorization"></a>uwierzytelnianie i autoryzacja gRPC

uwierzytelnianie i autoryzacja gRPC odbywają się na dwóch poziomach:

* Uwierzytelnianie na poziomie wywołań/Autoryzacja jest zwykle obsługiwana za pomocą tokenów, które są stosowane w metadanych podczas wywołania. 
* Uwierzytelnianie na poziomie kanału używa certyfikatu klienta, który jest stosowany na poziomie połączenia. Może również uwzględniać poświadczenia uwierzytelniania/autoryzacji na poziomie wywołań, które mają być stosowane do każdego wywołania w kanale automatycznie. 

Można użyć jednego lub obu tych mechanizmów, aby pomóc w zabezpieczeniu usługi.

ASP.NET Core implementacja gRPC obsługuje uwierzytelnianie i autoryzację za pomocą większości standardowych mechanizmów ASP.NET Core:

- Uwierzytelnianie wywołań
  - Azure Active Directory
  - IdentityServer
  - Token okaziciela JWT
  - OAuth 2.0
  - OpenID Connect
  - WS-Federation
- Uwierzytelnianie kanałów
  - certyfikat klienta

Metody uwierzytelniania wywołań są wszystkie oparte na *tokenach*. Jedyną rzeczywistą różnicą jest to, w jaki sposób generowane są tokeny, oraz biblioteki, które są używane do weryfikacji tokenów w usłudze ASP.NET Core.

Aby uzyskać więcej informacji, zobacz artykuł dotyczący [uwierzytelniania i autoryzacji](/aspnet/core/grpc/authn-and-authz) .

> [!NOTE]
> W przypadku korzystania z gRPC za pośrednictwem protokołu HTTP/2 zaszyfrowanego przy użyciu protokołu TLS cały ruch między klientami a serwerami jest szyfrowany, nawet jeśli nie jest używane uwierzytelnianie na poziomie kanału.

W tym rozdziale przedstawiono sposób stosowania poświadczeń wywołań i poświadczeń kanału do usługi gRPC. Pokazano również, jak używać poświadczeń z klienta programu .NET Core gRPC do uwierzytelniania w usłudze.

>[!div class="step-by-step"]
>[Poprzednie](client-libraries.md)
>[dalej](call-credentials.md)
