---
title: Program obsługi tokenów sieci Web JSON
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 3dc76f3de714fd91d397cc240d02a1a8605fe18b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045333"
---
# <a name="json-web-token-handler"></a>Program obsługi tokenów sieci Web JSON
Rozszerzenie JSON Web Token Handler dla programu Windows Identity Foundation umożliwia tworzenie i weryfikowanie tokenów sieci Web w formacie JSON (JWT) w tworzonych aplikacjach. Rozszerzenie JWT Token Handler można skonfigurować do uruchamiania w potoku programu WIF, podobnie jak inne wbudowane programy obsługi tokenów zabezpieczających, ale można go również używać niezależnie w celu walidacji tokenów w aplikacjach zubożonych. Rozszerzenie JWT Token Handler jest szczególnie przydatne w przypadku korzystania ze schematu tokenu okaziciela protokołu OAuth 2.0, na przykład podczas uwierzytelniania w usłudze Active Directory systemu Microsoft Azure.  
  
 Rozszerzenie JWT Token Handler jest dostępne jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz artykuł [Pobieranie pakietu obsługi tokenów sieci Web JSON](downloading-the-json-web-token-handler-package.md) .  
  
## <a name="scenarios"></a>Scenariusze  
 Rozszerzenie JWT Token Handler umożliwia realizację następujących podstawowych scenariuszy:  
  
- **Sprawdź poprawność tokenu JWT w aplikacji serwera**: W tym scenariuszu firma o nazwie litware ma aplikację serwerową, która używa WIF do obsługi żądań logowania w sieci Web. Firma Litware chce umożliwić swojej aplikacji używanie tokenów JWT do uwierzytelniania. Aplikacja zostaje zaktualizowana za pomocą rozszerzenia JWT Token Handler, a następnie zostaje aktualizowana konfiguracja aplikacji w celu dodania tego rozszerzenia do potoku programu WIF. Po dokonaniu aktualizacji, gdy nowe żądanie wchodzi do potoku programu WIF, token JWT jest weryfikowany przy użyciu nowego programu obsługi i zostaje pomyślnie uwierzytelniany.  
  
- **Sprawdzanie poprawności tokenu JWT w usłudze sieci Web REST**: W tym scenariuszu firma o nazwie litware ma usługę sieci Web REST, która jest zabezpieczona przez Azure Active Directory systemu Windows. Żądania kierowane do tej usługi sieci Web muszą być uwierzytelniane przez usługę AD systemu Microsoft Azure, która po pomyślnym uwierzytelnieniu wystawia token JWT. Firma Litware ma aplikację klienta, która musi uzyskać dostęp do tej usługi sieci Web. Klient wysyła żądanie do usługi sieci Web i przedstawia token JWT z usługi AD systemu Microsoft Azure, który zostaje zweryfikowany przez usługę sieci Web przy użyciu rozszerzenia JWT Token Handler. Po zweryfikowaniu tokenu przez rozszerzenie JWT Token Handler żądany zasób jest zwracany do klienta przez usługę sieci Web.  
  
## <a name="features"></a>Funkcje  
 Rozszerzenie JWT Token Handler oferuje następujące funkcje:  
  
- **Sprawdź poprawność tokenu JWT**: Tokeny JWT mogą być łatwe do zweryfikowania przez logikę sprawdzania poprawności procedury obsługi tokenu, jako część potoku WIF aplikacji lub wywoływana niezależnie od WIF  
  
- **Utwórz token JWT**: Program obsługi tokenów JWT może służyć do tworzenia tokenów JWT na potrzeby autoryzacji w usługach podrzędnych
