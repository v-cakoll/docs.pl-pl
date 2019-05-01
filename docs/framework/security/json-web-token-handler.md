---
title: Program obsługi tokenów sieci Web JSON
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 27c01a3d0ce0f2891b00ad28526d4753b9be4ce0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790133"
---
# <a name="json-web-token-handler"></a>Program obsługi tokenów sieci Web JSON
Rozszerzenie JSON Web Token Handler dla programu Windows Identity Foundation umożliwia tworzenie i weryfikowanie tokenów sieci Web w formacie JSON (JWT) w tworzonych aplikacjach. Rozszerzenie JWT Token Handler można skonfigurować do uruchamiania w potoku programu WIF, podobnie jak inne wbudowane programy obsługi tokenów zabezpieczających, ale można go również używać niezależnie w celu walidacji tokenów w aplikacjach zubożonych. Rozszerzenie JWT Token Handler jest szczególnie przydatne w przypadku korzystania ze schematu tokenu okaziciela protokołu OAuth 2.0, na przykład podczas uwierzytelniania w usłudze Active Directory systemu Microsoft Azure.  
  
 Rozszerzenie JWT Token Handler jest dostępne jako pakiet NuGet. Zobacz [Pobieranie pakietu JSON Web Token obsługi](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) Aby uzyskać więcej informacji.  
  
## <a name="scenarios"></a>Scenariusze  
 Rozszerzenie JWT Token Handler umożliwia realizację następujących podstawowych scenariuszy:  
  
- **Weryfikacja tokenu JWT w aplikacji serwera**: W tym scenariuszu firma o nazwie Litware ma aplikację serwera, który używa programu WIF do obsługi żądań logowania jednokrotnego sieci web. Firma Litware chce umożliwić swojej aplikacji używanie tokenów JWT do uwierzytelniania. Aplikacja zostaje zaktualizowana za pomocą rozszerzenia JWT Token Handler, a następnie zostaje aktualizowana konfiguracja aplikacji w celu dodania tego rozszerzenia do potoku programu WIF. Po dokonaniu aktualizacji, gdy nowe żądanie wchodzi do potoku programu WIF, token JWT jest weryfikowany przy użyciu nowego programu obsługi i zostaje pomyślnie uwierzytelniany.  
  
- **Weryfikacja tokenu JWT w usłudze sieci Web REST**: W tym scenariuszu firma o nazwie Litware ma usługę sieci web REST, która jest zabezpieczony przez usługi Windows Azure Active Directory. Żądania kierowane do tej usługi sieci Web muszą być uwierzytelniane przez usługę AD systemu Microsoft Azure, która po pomyślnym uwierzytelnieniu wystawia token JWT. Firma Litware ma aplikację klienta, która musi uzyskać dostęp do tej usługi sieci Web. Klient wysyła żądanie do usługi sieci Web i przedstawia token JWT z usługi AD systemu Microsoft Azure, który zostaje zweryfikowany przez usługę sieci Web przy użyciu rozszerzenia JWT Token Handler. Po zweryfikowaniu tokenu przez rozszerzenie JWT Token Handler żądany zasób jest zwracany do klienta przez usługę sieci Web.  
  
## <a name="features"></a>Funkcje  
 Rozszerzenie JWT Token Handler oferuje następujące funkcje:  
  
- **Weryfikacja tokenu JWT**: Tokeny JWT mogą być łatwo weryfikowane przez logikę weryfikacji programu obsługi tokenów, albo jako część potoku programu WIF aplikacji lub wywołanego niezależnie od programu WIF  
  
- **Utwórz token JWT Token**: Rozszerzenie JWT Token Handler może służyć do tworzenia tokenów JWT na potrzeby autoryzacji w usługach niższego rzędu
