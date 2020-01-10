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
ms.openlocfilehash: 1dfb1f6246e86d6f565c9338fb09f34a1608e9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705928"
---
# <a name="role-based-security"></a>Zabezpieczenia oparte na rolach
Role są często używane w aplikacjach finansowych lub firmowych w celu wymuszenia zasad. Na przykład aplikacja może nakładać limity rozmiaru przetwarzanej transakcji w zależności od tego, czy użytkownik wysyłający żądanie jest członkiem określonej roli. Urzędy mogą mieć autoryzację, aby przetwarzać transakcje, które są mniejsze od określonego progu, kierownicy mogą mieć wyższy limit, a wiceprezesowie mogą mieć jeszcze wyższy limit (lub bez ograniczeń). Zabezpieczeń opartych na rolach można także użyć, gdy aplikacja wymaga wielu zatwierdzeń do ukończenia akcji. Taki przypadek może być systemem zakupów, w którym każdy pracownik może wygenerować żądanie zakupu, ale tylko agent zakupów może przekonwertować to żądanie na zamówienie zakupu, które może zostać wysłane do dostawcy.  
  
 .NET Framework zabezpieczenia oparte na rolach obsługują autoryzację, tworząc informacje o podmiotu zabezpieczeń, który jest zbudowany ze skojarzonej tożsamości, dostępnej dla bieżącego wątku. Tożsamość (oraz podmiot zabezpieczeń, które ułatwiają zdefiniowanie) mogą być oparte na koncie systemu Windows lub być niestandardową tożsamością niepowiązaną z kontem systemu Windows. Aplikacje .NET Framework mogą podejmować decyzje dotyczące autoryzacji na podstawie tożsamości podmiotu zabezpieczeń lub członkostwa w rolach lub obu tych metod. Rola to nazwany zestaw podmiotów zabezpieczeń, który ma takie same uprawnienia, w odniesieniu do zabezpieczeń (takich jak Kasjer lub kierownik). Podmiot zabezpieczeń może być członkiem jednej lub większej liczby ról. W związku z tym aplikacje mogą używać przynależności do roli, aby określić, czy podmiot zabezpieczeń jest autoryzowany do wykonywania żądanych akcji.  
  
 Aby zapewnić łatwość użycia i spójność z zabezpieczeniami dostępu kodu, .NET Framework zabezpieczenia oparte na rolach zapewniają <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> obiektów, które umożliwiają środowisko uruchomieniowe języka wspólnego wykonywanie autoryzacji w sposób podobny do sprawdzania zabezpieczeń dostępu kodu. Klasa <xref:System.Security.Permissions.PrincipalPermission> reprezentuje tożsamość lub rolę, która musi być zgodna z podmiotem zabezpieczeń i jest zgodna z kontrolami bezpieczeństwa deklaracyjnego i bezwzględnego. Dostęp do informacji o tożsamości podmiotu zabezpieczeń można także uzyskać bezpośrednio, a w razie konieczności sprawdzać rolę i tożsamość w kodzie.  
  
 .NET Framework zapewnia obsługę zabezpieczeń opartą na rolach, która jest elastyczna i rozszerzalna, aby zaspokoić potrzeby szerokiego spektrum aplikacji. Możesz zdecydować się na współdziałanie z istniejącymi infrastrukturami uwierzytelniania, takimi jak usługi COM+ 1,0, lub utworzyć niestandardowy system uwierzytelniania. Zabezpieczenia oparte na rolach są szczególnie odpowiednie do użycia w aplikacjach sieci Web ASP.NET, które są przetwarzane głównie na serwerze programu. Jednak zabezpieczenia oparte na rolach .NET Framework mogą być używane zarówno na kliencie, jak i na serwerze.  
  
 Przed przeczytaniem tej sekcji należy zapoznać się z materiałami przedstawionymi w [najważniejszych pojęciach dotyczących zabezpieczeń](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)|W tym artykule wyjaśniono, jak skonfigurować zarówno system Windows, jak i tożsamości ogólne oraz podmioty zabezpieczeń.|  
|[Główne pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md)|Wprowadza podstawowe pojęcia, które należy zrozumieć przed użyciem .NET Framework zabezpieczenia.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
