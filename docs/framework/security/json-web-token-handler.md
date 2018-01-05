---
title: "Program obsługi tokenów sieci Web JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a822e87f03c4fa7e1ce7449f09efd178b87cc99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="json-web-token-handler"></a>Program obsługi tokenów sieci Web JSON
Rozszerzenie JSON Web Token Handler dla programu Windows Identity Foundation umożliwia tworzenie i weryfikowanie tokenów sieci Web w formacie JSON (JWT) w tworzonych aplikacjach. Rozszerzenie JWT Token Handler można skonfigurować do uruchamiania w potoku programu WIF, podobnie jak inne wbudowane programy obsługi tokenów zabezpieczających, ale można go również używać niezależnie w celu walidacji tokenów w aplikacjach zubożonych. Rozszerzenie JWT Token Handler jest szczególnie przydatne w przypadku korzystania ze schematu tokenu okaziciela protokołu OAuth 2.0, na przykład podczas uwierzytelniania w usłudze Active Directory systemu Microsoft Azure.  
  
 Rozszerzenie JWT Token Handler jest dostępne jako pakiet NuGet. Zobacz [Pobieranie pakietu JSON Web Token programu obsługi](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) Aby uzyskać więcej informacji.  
  
## <a name="scenarios"></a>Scenariusze  
 Rozszerzenie JWT Token Handler umożliwia realizację następujących podstawowych scenariuszy:  
  
-   **Sprawdzanie poprawności w aplikacji serwera tokenu JWT**: W tym scenariuszu firma Litware ma aplikacji serwera, która używa WIF do obsługi żądań logowania jednokrotnego w sieci web. Firma Litware chce umożliwić swojej aplikacji używanie tokenów JWT do uwierzytelniania. Aplikacja zostaje zaktualizowana za pomocą rozszerzenia JWT Token Handler, a następnie zostaje aktualizowana konfiguracja aplikacji w celu dodania tego rozszerzenia do potoku programu WIF. Po dokonaniu aktualizacji, gdy nowe żądanie wchodzi do potoku programu WIF, token JWT jest weryfikowany przy użyciu nowego programu obsługi i zostaje pomyślnie uwierzytelniany.  
  
-   **Sprawdzanie poprawności tokenu JWT usługi sieci Web REST**: W tym scenariuszu firma Litware ma usługi sieci web REST jest zabezpieczony przez Windows Azure Active Directory. Żądania kierowane do tej usługi sieci Web muszą być uwierzytelniane przez usługę AD systemu Microsoft Azure, która po pomyślnym uwierzytelnieniu wystawia token JWT. Firma Litware ma aplikację klienta, która musi uzyskać dostęp do tej usługi sieci Web. Klient wysyła żądanie do usługi sieci Web i przedstawia token JWT z usługi AD systemu Microsoft Azure, który zostaje zweryfikowany przez usługę sieci Web przy użyciu rozszerzenia JWT Token Handler. Po zweryfikowaniu tokenu przez rozszerzenie JWT Token Handler żądany zasób jest zwracany do klienta przez usługę sieci Web.  
  
## <a name="features"></a>Funkcje  
 Rozszerzenie JWT Token Handler oferuje następujące funkcje:  
  
-   **Sprawdzanie poprawności tokenu JWT**: tokenów JWT można łatwo zweryfikowany przez logikę weryfikacji tokenu programu obsługi, w ramach aplikacji WIF potoku lub wywołać niezależnie od WIF  
  
-   **Utwórz JWT Token**: program obsługi tokenów JWT może służyć do tworzenia tokenów JWT do autoryzacji w usługach podrzędne
