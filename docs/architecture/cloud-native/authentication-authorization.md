---
title: Uwierzytelnianie i autoryzacja w aplikacjach natywnych dla chmury
description: Projektowanie aplikacji platformy .NET natywnych dla chmury na platformie Azure | Uwierzytelnianie i autoryzacja w aplikacjach natywnych w chmurze
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805545"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Uwierzytelnianie i autoryzacja w aplikacjach natywnych dla chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

*Uwierzytelnianie* to proces określania tożsamości podmiotu zabezpieczeń. *Autoryzacja* jest aktem udzielania uwierzytelnionego uprawnienia głównego do wykonywania akcji lub uzyskiwania dostępu do zasobu. Czasami uwierzytelnianie jest `AuthN` skrócone, a `AuthZ`autoryzacja jest skracana do . Aplikacje natywne w chmurze muszą polegać na otwartych protokołach opartych na protokole HTTP w celu uwierzytelnienia podmiotów zabezpieczeń, ponieważ zarówno klienci, jak i aplikacje mogą być uruchomione w dowolnym miejscu na świecie na dowolnej platformie lub urządzeniu. Jedynym częstym czynnikiem jest HTTP.

Wiele organizacji nadal korzysta z lokalnych usług uwierzytelniania, takich jak Usługi federacyjne Active Directory (ADFS). Chociaż takie podejście tradycyjnie służył organizacjom dobrze na potrzeby uwierzytelniania lokalnego, aplikacje natywne w chmurze korzystają z systemów zaprojektowanych specjalnie dla chmury. Niedawne doradztwo Narodowego Centrum Bezpieczeństwa Cybernetycznego (NCSC) 2019 stwierdza, że "organizacje korzystające z usługi Azure AD jako głównego źródła uwierzytelniania faktycznie obniżą swoje ryzyko w porównaniu z usługą ADFS". Niektóre powody opisane w [tej analizie](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) obejmują:

- Dostęp do pełnego zestawu technologii ochrony poświadczeń firmy Microsoft.
- Większość organizacji już w pewnym stopniu polega na usłudze Azure AD.
- Podwójne mieszanie skrótów NTLM gwarantuje, że kompromis nie pozwoli na poświadczenia, które działają w lokalnej usłudze Active Directory.

## <a name="references"></a>Dokumentacja

- [Podstawowe informacje o uwierzytelnianiu](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Dostęp do tokenów i oświadczeń](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Być może nadszedł czas, aby porzucić usługi uwierzytelniania lokalnego](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Poprzedni](identity.md)
>[następny](azure-active-directory.md)
