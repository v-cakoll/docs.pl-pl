---
title: Zabezpieczenia w aplikacjach gRPC — gRPC dla deweloperów WCF
description: Omówienie uwierzytelniania wywołań i kanałów oraz autoryzacji w programie gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f3d32817ccb5d9f278d256c0ee135f0e2a17cf2
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184142"
---
# <a name="security-in-grpc-applications"></a>Zabezpieczenia w aplikacjach gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W dowolnym rzeczywistym scenariuszu Zabezpieczanie aplikacji i usług jest niezbędne. Zabezpieczenia obejmują trzy kluczowe obszary: szyfrowanie ruchu sieciowego w celu uniemożliwienia jego przechwytywania przez złe uczestników; Uwierzytelnianie klientów i serwerów w celu ustanowienia tożsamości i zaufania; i Autoryzuj klientów do kontrolowania dostępu do systemów i stosowania uprawnień na podstawie tożsamości.

> [!NOTE]
> **Uwierzytelnianie** dotyczy ustanowienia tożsamości klienta lub serwera. **Autoryzacja** jest zaangażowana w ustalanie, czy klient ma uprawnienia dostępu do zasobu, czy wydać polecenie.

Ten rozdział obejmuje funkcje uwierzytelniania i autoryzacji w programie gRPC dla ASP.NET Core i omówienia zabezpieczeń sieci przy użyciu szyfrowanych połączeń TLS.

## <a name="wcf-authentication-and-authorization"></a>Uwierzytelnianie i autoryzacja w programie WCF

W programie WCF uwierzytelnianie i autoryzacja zostały obsłużone na różne sposoby w zależności od używanych transportów i powiązań. Obsługiwane są różne standardy protokołu\* WS-Security, a także uwierzytelnianie systemu Windows dla usług http uruchomionych w usługach IIS lub NetTCP Services między systemami Windows.

## <a name="grpc-authentication-and-authorization"></a>uwierzytelnianie i autoryzacja gRPC

uwierzytelnianie i autoryzacja gRPC działają na dwóch poziomach. Uwierzytelnianie na poziomie wywołań/Autoryzacja jest zwykle obsługiwana przy użyciu tokenów, które są stosowane w metadanych podczas wywołania. Uwierzytelnianie na poziomie kanału używa certyfikatu klienta, który jest stosowany na poziomie połączenia, i może również obejmować poświadczenia uwierzytelniania/autoryzacji na poziomie wywołań, które mają być stosowane do każdego wywołania w kanale automatycznie. Do zabezpieczenia usługi można użyć jednego lub obu tych mechanizmów.

ASP.NET Core implementacja gRPC obsługuje uwierzytelnianie i autoryzację przy użyciu większości standardowych mechanizmów ASP.NET Core:

- Uwierzytelnianie wywołań
  - Azure Active Directory
  - IdentityServer
  - Token okaziciela JWT
  - OAuth 2,0
  - OpenID Connect połączenie
  - WS-Federation
- Uwierzytelnianie kanałów
  - Certyfikat klienta

Metody uwierzytelniania wywołań są wszystkie oparte na *tokenach*. Jedyną rzeczywistą różnicą jest to, w jaki sposób generowany jest token, oraz biblioteki, które są używane do weryfikacji tokenów w usłudze ASP.NET Core.

Aby uzyskać więcej informacji, zobacz [dokumentację dotyczącą uwierzytelniania i autoryzacji na Microsoft docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).

> [!NOTE]
> W przypadku korzystania z gRPC za pośrednictwem protokołu HTTP/2 zaszyfrowanego przy użyciu protokołu TLS cały ruch między klientami a serwerami jest szyfrowany, nawet jeśli nie jest używane uwierzytelnianie na poziomie kanału.

W tym rozdziale pokazano, jak zastosować poświadczenia wywołania i poświadczenia kanału do usługi gRPC oraz jak używać poświadczeń z klienta platformy .NET Core gRPC do uwierzytelniania w usłudze.

>[!div class="step-by-step"]
>[Poprzedni](client-libraries.md)
>[Następny](call-credentials.md)
