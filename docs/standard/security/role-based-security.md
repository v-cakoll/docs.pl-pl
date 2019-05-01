---
title: Zabezpieczenia oparte na rolach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596165bfac9c65898448714a4477b7f045bd87d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018583"
---
# <a name="role-based-security"></a>Zabezpieczenia oparte na rolach
Role są często używane w aplikacjach finansowe lub biznesowych do wymuszania zasad. Na przykład aplikacja może nałożyć limitów rozmiaru transakcji przetwarzanych w zależności od tego, czy użytkownika zgłaszającego żądanie jest członkiem określonej roli. Urzędników może mieć upoważnienie do przetwarzania transakcji, których wartość jest mniejsza niż określony próg, nadzorców może mieć wyższy limit i wiceprzewodniczący może być nadal wyższy limit (lub brak limitu w ogóle). Zabezpieczenia oparte na roli można także jeśli aplikacja wymaga wielu zatwierdzeń do zakończenia akcji. Takiej sytuacji może być systemu zakupów, w którym każdy pracownik może wygenerować żądanie zakupu, ale tylko zakupu agenta można przekształcić to żądanie w zamówienia zakupu, które mogą być wysyłane do dostawcy.  
  
 Zabezpieczenia oparte na roli platformy .NET framework obsługuje autoryzacji, wprowadzając informacje podmiotu zabezpieczeń, które są konstruowane na podstawie skojarzonego tożsamości, dostępne dla bieżącego wątku. Tożsamość (i jednostki, które warto zdefiniować) może być to oparte na konta Windows, lub być tożsamość niestandardowa niepowiązane z kontem Windows. Aplikacje programu .NET framework ułatwia oparte na tożsamości podmiotu zabezpieczeń, członkostwo w roli lub obu tych decyzji dotyczących autoryzacji. Rola to nazwany zestaw podmiotów zabezpieczeń, które mają takie same uprawnienia w odniesieniu do zabezpieczeń (na przykład dla kasjerów lub Menedżera). Podmiot zabezpieczeń może należeć do jednej lub większej liczby ról. W związku z tym aplikacje mogą używać członkostwo w rolach, aby ustalić, czy podmiot zabezpieczeń jest autoryzowany do wykonania żądanej akcji.  
  
 Aby zapewnić łatwość użycia i spójność zabezpieczenia dostępu kodu, zabezpieczenia oparte na roli platformy .NET Framework zapewnia <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> obiekty, które umożliwiają środowiska uruchomieniowego języka wspólnego przeprowadzić autoryzację w sposób podobny do kodu dostępu sprawdzanie zabezpieczeń. <xref:System.Security.Permissions.PrincipalPermission> Klasa reprezentuje tożsamość lub roli, czy podmiot zabezpieczeń musi odpowiadać i jest zgodny z obydwu kontroli zabezpieczeń deklaratywnego i imperatywnego. Można także bezpośredni dostęp do informacji o tożsamości podmiotu zabezpieczeń i wykonywać roli i tożsamości sprawdza, czy w kodzie, gdy potrzebne.  
  
 .NET Framework zapewnia obsługę opartej na rolach zabezpieczeń, który jest elastyczny i rozszerzalny, aby zaspokoić potrzeby szerokiego spektrum aplikacji. Można na potrzeby współdziałania z istniejącej infrastruktury uwierzytelniania, takich jak usług COM + 1.0, lub utworzyć niestandardowy system uwierzytelniania. Zabezpieczenia oparte na rolach jest przeznaczone szczególnie do użycia w aplikacji sieci Web platformy ASP.NET, które są przetwarzane przede wszystkim na serwerze. Zabezpieczenia oparte na roli platformy .NET Framework można jednak po stronie klienta lub serwera.  
  
 Przed przeczytaniem tej części, upewnij się, że rozumiesz materiał znajdujące się w [podstawowe pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)|Wyjaśnia, jak skonfigurować i zarządzać nimi, Windows i ogólny tożsamości i nazwy główne.|  
|[Główne pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md)|Wprowadzono podstawowe pojęcia, które należy zrozumieć przed rozpoczęciem korzystania z zabezpieczeń .NET Framework.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
