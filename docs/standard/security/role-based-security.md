---
title: Zabezpieczenia oparte na rolach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 83a3f58fc13eb1aaacb99a3f35c3149d78451c23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="role-based-security"></a>Zabezpieczenia oparte na rolach
Role są często używane w aplikacjach finansowych lub pracy do wymuszania zasad. Na przykład aplikacja może nałożyć limity rozmiaru transakcji przetwarzanych w zależności od tego, czy użytkownik zgłoszenia żądania jest członkiem określonej roli. Urzędników może być autoryzacji do przetwarzania transakcji, które mają mniej niż określony próg kierownicy mogą mieć wyższy limit i zastępców prezesa może być nadal wyższy limit (lub brak limitu wcale). Oparta na rolach zabezpieczeń można także jeśli aplikacja wymaga zatwierdzenia wielu ukończyć akcji. Taki przypadek może być systemu zakupów, w którym każdy pracownik może wygenerować żądania zakupu, ale tylko agent zakupów można przekształcić tego żądania w zamówienia zakupu, które mogą być wysyłane do dostawcy.  
  
 Zabezpieczenia oparte na rolach .NET framework obsługuje autoryzacji informacji o podmiot zabezpieczeń, który jest tworzony z tożsamością skojarzone dostępne dla bieżącego wątku. Tożsamość (podmiot zabezpieczeń, który umożliwia definiowanie) może być albo oparta na konto systemu Windows i jest tożsamość niestandardowa niezwiązanych ze sobą na konto systemu Windows. Aplikacji .NET framework podjęcie decyzji dotyczących autoryzacji na podstawie tożsamości podmiotu lub członkostwo roli lub oba. Rola to nazwany zestaw podmiotów zabezpieczeń, które mają te same uprawnienia względem zabezpieczeń (na przykład dla kasjerów lub Menedżera). Podmiot zabezpieczeń może należeć do jednej lub więcej ról. W związku z tym aplikacje mogą używać członkostwo roli, aby określić, czy podmiot zabezpieczeń jest autoryzowany do wykonania żądanej akcji.  
  
 Aby zapewnić łatwość użycia i spójność z zabezpieczeniami dostępu kodu, zapewnia zabezpieczenia oparte na rolach .NET Framework <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> obiektów, które umożliwiają środowisko uruchomieniowe języka wspólnego w celu wykonania autoryzacji w taki sposób, który jest podobny do kodu dostępu kontroli zabezpieczeń. <xref:System.Security.Permissions.PrincipalPermission> Klasa reprezentuje tożsamość lub roli, czy podmiot zabezpieczeń musi być zgodny i jest zgodny z obydwu kontroli zabezpieczenia deklaratywne i bezwzględne. Można również bezpośrednio uzyskać dostępu do informacji o tożsamości podmiotu zabezpieczeń i wykonywać roli i tożsamości sprawdza w kodzie, gdy jest wymagane.  
  
 .NET Framework zapewnia obsługę opartej na rolach zabezpieczeń, która jest elastyczny i rozszerzalny odpowiadających potrzebom szerokiego zakresu aplikacji. Można na potrzeby współdziałania z istniejącej infrastruktury uwierzytelniania, takich jak usług COM + 1.0, lub można utworzyć systemu uwierzytelniania niestandardowego. Zabezpieczenia oparte na rolach jest szczególnie dobrze nadaje się do użycia w aplikacji sieci Web ASP.NET, które są przetwarzane przede wszystkim na serwerze. .NET Framework opartej na rolach zabezpieczeń można jednak po stronie klienta lub serwera.  
  
 Przed przeczytaniem tej części, upewnij się, że rozumiesz, materiałów przedstawionych w [podstawowe pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)|Opisano sposób konfigurowania i zarządzania systemu Windows i rodzajowy tożsamości i podmiotów zabezpieczeń.|  
|[Główne pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md)|Wprowadzono podstawowe pojęcia, które należy zrozumieć przed rozpoczęciem korzystania z zabezpieczeń .NET Framework.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
