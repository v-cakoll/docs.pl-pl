---
title: Główne pojęcia dotyczące zabezpieczeń
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c483baeca9efcbc4a38020a7b2f4fa221a6b4028
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018622"
---
# <a name="key-security-concepts"></a>Główne pojęcia dotyczące zabezpieczeń
Microsoft .NET Framework oferuje opartej na rolach zabezpieczeń, ułatwiających adresu z punktu widzenia bezpieczeństwa kod aplikacji mobilnych i świadczenia pomocy technicznej, umożliwiająca składników ustalić, użytkownicy są autoryzowane w celu.  
  
## <a name="type-safety-and-security"></a>Zabezpieczenia i ochrona typu  
 Kod bezpiecznego typu uzyskuje dostęp do lokalizacji pamięci, który jest upoważniony do dostępu. (Dla tej dyskusji, bezpieczeństwo typów specjalnie odwołuje się do bezpieczeństwa typu pamięci i nie należy mylić z bezpieczeństwem typu w szerszym zakresie.) Na przykład kod bezpiecznego typu nie można odczytać wartości z prywatnych pól innego obiektu. Uzyskuje dostęp do typów wyłącznie na wyraźnie określone, dozwolone sposoby.  
  
 Podczas just-in-time (JIT) kompilacja, opcjonalny proces weryfikacji analizuje metadane i język Microsoft intermediate language (MSIL) metody, aby być skompilowana JIT w macierzystym kodzie maszynowym, aby zweryfikować, że są bezpieczne dla typów. Ten proces jest pomijany, jeśli kod ma uprawnienie pomijania weryfikacji. Aby uzyskać więcej informacji na temat weryfikacji, zobacz [Managed Execution Process](../../../docs/standard/managed-execution-process.md).  
  
 Chociaż potwierdzenie bezpieczeństwa typu nie jest obowiązkowe, aby uruchomić kod zarządzany, bezpieczeństwo typów odgrywa kluczową rolę w izolacji zestawu oraz wzmacnianiu zabezpieczeń. Gdy kod jest bezpiecznym typem, środowisko uruchomieniowe języka wspólnego może całkowicie odizolować zestawy od siebie nawzajem. Izolacja pomaga upewnić się, że zestawy nie może mieć negatywny wpływ na siebie nawzajem i zwiększać niezawodności aplikacji. Składniki typu palety można wykonać bezpiecznie w tym samym procesie, nawet jeśli są one zaufane na różnych poziomach. Jeżeli kod nie jest bezpiecznym typem, mogą wystąpić niepożądane skutki uboczne. Na przykład środowisko uruchomieniowe nie może uniemożliwić kodu zarządzanego z wywołaniem do kodu natywnego (niezarządzanego) i wykonaniu złośliwych operacji. Gdy kod jest bezpiecznym typem, mechanizm wymuszania zabezpieczenia środowiska wykonawczego gwarantuje, że jej nie dostępu do kodu macierzystego, chyba że ma uprawnienia, aby to zrobić. Cały kod, który nie jest typem bezpiecznym musiał otrzymać <xref:System.Security.Permissions.SecurityPermission> z elementem członkowskim wyliczenia przekazany <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> do uruchomienia.  
  
 Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Główne  
 Podmiot zabezpieczeń reprezentuje tożsamość i rolę użytkownika i działa w imieniu użytkownika. Oparta na rolach zabezpieczeń w programie .NET Framework obsługuje trzy rodzaje jednostek:  
  
- Ogólne jednostki reprezentują użytkowników i ról, które istnieją niezależnie od Windows użytkownikami i rolami.  
  
- Windows podmiotów zabezpieczeń reprezentuje użytkowników Windows i ich ról (lub ich grupy Windows). Podmiot zabezpieczeń Windows mogą personifikować innego użytkownika, co oznacza że podmiot zabezpieczeń może uzyskiwać dostęp do zasobów w imieniu użytkownika, podczas zaprezentowanie tożsamości, która należy do tego użytkownika.  
  
- Jednostki niestandardowe mogą być definiowane przez aplikację w jakikolwiek sposób, który jest wymagany dla określonej aplikacji. Mogą one rozszerzać podstawowe pojęcie tożsamości podmiotu zabezpieczeń i role.  
  
 Aby uzyskać więcej informacji, zobacz [podmiot zabezpieczeń i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Uwierzytelnianie  
 Uwierzytelnianie to proces odnajdywania i weryfikowania tożsamości podmiotu zabezpieczeń, sprawdzając poświadczenia użytkownika i sprawdzanie poprawności tych poświadczeń względem niektórych urzędu. Informacje uzyskane podczas uwierzytelniania nadaje się bezpośrednio w kodzie. Umożliwia także .NET Framework oparta na rolach zabezpieczeń do uwierzytelniania bieżącego użytkownika i do ustalenia, czy należy zezwolić tego obiektu głównego dostęp do Twojego kodu. Zobacz przeciążenia <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> metoda przykładów dotyczących sposobów uwierzytelniania podmiotu zabezpieczeń dla określonych ról. Na przykład, można użyć <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> przeciążenia do ustalenia, czy bieżący użytkownik jest członkiem grupy Administratorzy.  
  
 Różnych mechanizmów uwierzytelniania są obecnie używane, z których wiele mogą być używane z zabezpieczeń opartych na roli platformy .NET Framework. Niektóre z najczęściej używanych mechanizmów są podstawowe, szyfrowane, usługi Passport, system operacyjny (na przykład protokołu NTLM lub Kerberos) lub mechanizmów zdefiniowanych przez aplikację.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wymaga aktywny podmiot zabezpieczeń administratora. `name` Parametr jest `null`, co pozwala każdy użytkownik, który jest administratorem, aby przekazać żądanie.  
  
> [!NOTE]
>  W systemie Windows Vista kontroli konta użytkownika (UAC) określa uprawnienia użytkownika. Jeśli jesteś członkiem wbudowanej grupy Administratorzy, masz przypisane dwa tokeny dostępu w czasie wykonywania: token dostępu użytkownika standardowego i token dostępu administratora. Domyślnie jesteś w roli użytkownika standardowego. Do wykonania kodu, musisz być administratorem, musisz najpierw podwyższenie swoje uprawnienia z użytkownika standardowego do administratora. Można to zrobić, po uruchomieniu aplikacji, kliknij prawym przyciskiem myszy ikonę aplikacji i wskazujący, że chcesz uruchomić jako administrator.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Poniższy przykład pokazuje, jak określić tożsamości podmiotu zabezpieczeń i role, które są dostępne dla podmiotu zabezpieczeń. Aplikacja w tym przykładzie, może być upewnij się, że bieżący użytkownik jest w roli, którą umożliwiający korzystanie z aplikacji.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autoryzacja  
 Autoryzacja to proces określania, czy podmiot zabezpieczeń może wykonać żądanej akcji. Autoryzacja następuje po uwierzytelnieniu i używa informacji o tożsamości podmiotu zabezpieczeń i role, aby określić, jakie zasoby mogą uzyskiwać dostęp do podmiotu zabezpieczeń. Zabezpieczenia oparte na roli platformy .NET Framework służy do implementowania autoryzacji.
