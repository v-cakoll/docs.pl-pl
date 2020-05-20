---
title: Uwierzytelnianie i autoryzacja w aplikacjach natywnych w chmurze
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Uwierzytelnianie i autoryzacja w natywnych aplikacjach w chmurze
ms.date: 05/13/2020
ms.openlocfilehash: e5254560ac82662e5e3ea6a25997516cd2b478b0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614308"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Uwierzytelnianie i autoryzacja w aplikacjach natywnych dla chmury

*Uwierzytelnianie* to proces określania tożsamości podmiotu zabezpieczeń. *Autoryzacja* to czynność udzielenia uwierzytelnionego uprawnienia podmiotowi do wykonania akcji lub uzyskania dostępu do zasobu. Czasami uwierzytelnianie jest skracane `AuthN` i autoryzacja jest skracana do `AuthZ` . Aplikacje natywne w chmurze muszą polegać na otwartych protokołach opartych na protokole HTTP w celu uwierzytelniania podmiotów zabezpieczeń, ponieważ zarówno klienci, jak i aplikacje mogą działać w dowolnym miejscu na świecie na dowolnej platformie lub urządzeniu. Jedynym wspólnym czynnikiem jest protokół HTTP.

W wielu organizacjach nadal opierają się lokalne usługi uwierzytelniania, takie jak Active Directory Federation Services (AD FS). Chociaż ta metoda ma tradycyjnie obsługiwane organizacje dotyczące lokalnych potrzeb związanych z uwierzytelnianiem, aplikacje natywne dla chmury korzystają z systemów zaprojektowanych specjalnie dla chmury. W ostatnim 2019 w Zjednoczonym Królestwie National cybernetycznymi Security Centre (NCSC) poradnik "Organizacje korzystające z usługi Azure AD jako podstawowego źródła uwierzytelniania" w rzeczywistości obniżą ryzyko w porównaniu z usługami ADFS ". Niektóre przyczyny przedstawione w [tej analizie](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) obejmują:

- Dostęp do pełnego zestawu technologii ochrony poświadczeń firmy Microsoft.
- Większość organizacji korzysta już z usługi Azure AD w pewnym zakresie.
- Podwójne mieszanie skrótów NTLM gwarantuje naruszenie nie będzie zezwalać na poświadczenia, które działają w lokalnym Active Directory.

## <a name="references"></a>Dokumentacja

- [Podstawowe informacje o uwierzytelnianiu](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Tokeny dostępu i oświadczenia](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Zrezygnować usług uwierzytelniania lokalnego może być czasochłonne](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Poprzedni](identity.md) 
> [Dalej](azure-active-directory.md)
