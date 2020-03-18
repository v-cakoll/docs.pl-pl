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
ms.openlocfilehash: b7bcb7e56ca14d129eadcaeac19452d4a443713d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400660"
---
# <a name="key-security-concepts"></a>Główne pojęcia dotyczące zabezpieczeń
Program Microsoft .NET Framework oferuje zabezpieczenia oparte na rolach, aby pomóc w rozwiązywaniu problemów związanych z bezpieczeństwem kodu komórkowego i zapewniać pomoc techniczną, która umożliwia składnikom określenie, do czego użytkownicy są autoryzowani.  
  
## <a name="type-safety-and-security"></a>Bezpieczeństwo typów i ochrony  
 Kod bezpieczny dla typu uzyskuje dostęp tylko do lokalizacji pamięci, do które jest upoważniony. (W tej dyskusji bezpieczeństwo typów odnosi się w szczególności do bezpieczeństwa typów pamięci i nie powinno być mylone z bezpieczeństwem typów w szerszym zakresie). Na przykład kod bezpieczny dla typu nie może odczytać wartości z pól prywatnych innego obiektu. Uzyskuje dostęp do typów tylko w dobrze zdefiniowany, dopuszczalny sposób.  
  
 Podczas kompilacji just-in-time (JIT) opcjonalny proces weryfikacji sprawdza metadane i język pośredni firmy Microsoft (MSIL) metody, która ma być skompilowana jit do natywnego kodu maszynowego, aby sprawdzić, czy są one bezpieczne dla typu. Ten proces jest pomijany, jeśli kod ma uprawnienia do pomijania weryfikacji. Aby uzyskać więcej informacji na temat weryfikacji, zobacz [Proces wykonania zarządzanego](../../../docs/standard/managed-execution-process.md).  
  
 Chociaż weryfikacja bezpieczeństwa typów nie jest obowiązkowa do uruchamiania kodu zarządzanego, bezpieczeństwo typów odgrywa kluczową rolę w izolacji zestawu i egzekwowaniu zabezpieczeń. Gdy kod jest bezpieczny typ, program uruchomieniowy języka wspólnego można całkowicie izolować zestawy od siebie. Ta izolacja pomaga zapewnić, że zestawy nie mogą niekorzystnie wpływać na siebie nawzajem i zwiększa niezawodność aplikacji. Składniki bezpieczne dla typu można bezpiecznie wykonać w tym samym procesie, nawet jeśli są one zaufane na różnych poziomach. Gdy kod nie jest typu bezpieczne, niepożądane skutki uboczne mogą wystąpić. Na przykład czas wykonywania nie może uniemożliwić kodu zarządzanego wywoływania do kodu macierzystego (niezarządzanego) i wykonywania złośliwych operacji. Gdy kod jest bezpieczny dla typu, mechanizm wymuszania zabezpieczeń w czasie wykonywania zapewnia, że nie ma dostępu do kodu macierzystego, chyba że ma do tego uprawnienia. Cały kod, który nie jest type <xref:System.Security.Permissions.SecurityPermission> safe musi być <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> przyznany z przekazanyelement członkowski wyliczenia do uruchomienia.  
  
 Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Główne  
 Podmiot zabezpieczeń reprezentuje tożsamość i rolę użytkownika i działa w imieniu użytkownika. Zabezpieczenia oparte na rolach w platformie .NET Framework obsługują trzy rodzaje podmiotów:  
  
- Ogólne podmioty reprezentują użytkowników i role, które istnieją niezależnie od użytkowników systemu Windows i ról.  
  
- Podmioty z grupy windows reprezentują użytkowników systemu Windows i ich role (lub ich grupy systemu Windows). Podmiot zabezpieczeń systemu Windows może personifikować innego użytkownika, co oznacza, że podmiot zabezpieczeń może uzyskać dostęp do zasobu w imieniu użytkownika podczas prezentacji tożsamości, która należy do tego użytkownika.  
  
- Podmioty niestandardowe mogą być zdefiniowane przez aplikację w dowolny sposób, który jest potrzebny dla tej konkretnej aplikacji. Mogą one rozszerzyć podstawowe pojęcie tożsamości i ról głównego zobowiązanego.  
  
 Aby uzyskać więcej informacji, zobacz [Obiekty główne i tożsamości](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Authentication  
 Uwierzytelnianie to proces odnajdowania i weryfikowania tożsamości podmiotu zabezpieczeń przez sprawdzenie poświadczeń użytkownika i sprawdzanie poprawności tych poświadczeń względem niektórych uprawnień. Informacje uzyskane podczas uwierzytelniania są bezpośrednio użyteczne przez kod. Można również użyć zabezpieczeń opartych na rolach platformy .NET Framework do uwierzytelniania bieżącego użytkownika i określić, czy zezwolić temu podmiotowi na dostęp do kodu. Zobacz przeciążenia <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> metody przykłady jak uwierzytelnić podmiot zabezpieczeń dla określonych ról. Na przykład można użyć <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> przeciążenia, aby określić, czy bieżący użytkownik jest członkiem grupy Administratorzy.  
  
 Obecnie używane są różne mechanizmy uwierzytelniania, z których wiele może być używanych z zabezpieczeniami opartymi na rolach .NET Framework. Niektóre z najczęściej używanych mechanizmów to podstawowe, szyfrowane, Paszport, system operacyjny (takich jak NTLM lub Kerberos) lub mechanizmy zdefiniowane przez aplikację.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wymaga, aby aktywny podmiot zabezpieczeń był administratorem. Parametr `name` jest `null`, co pozwala każdemu użytkownikowi, który jest administratorem, aby przekazać żądanie.  
  
> [!NOTE]
> W systemie Windows Vista kontrola konta użytkownika (UAC) określa uprawnienia użytkownika. Jeśli jesteś członkiem wbudowanej grupy Administratorzy, masz przypisane dwa tokeny dostępu w czasie wykonywania: token dostępu użytkownika standardowego i token dostępu administratora. Domyślnie jesteś w roli użytkownika standardowego. Aby wykonać kod, który wymaga bycia administratorem, należy najpierw podnieść swoje uprawnienia od użytkownika standardowego do administratora. Można to zrobić po uruchomieniu aplikacji, klikając prawym przyciskiem myszy ikonę aplikacji i wskazując, że chcesz uruchomić jako administrator.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 W poniższym przykładzie pokazano, jak określić tożsamość podmiotu zabezpieczeń i role dostępne dla podmiotu zabezpieczeń. Aplikacja w tym przykładzie może być, aby potwierdzić, że bieżący użytkownik jest w roli, którą zezwalasz na korzystanie z aplikacji.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autoryzacja  
 Autoryzacja to proces określania, czy podmiot zabezpieczeń może wykonać żądaną akcję. Autoryzacja występuje po uwierzytelnieniu i używa informacji o tożsamości i ról podmiotu zabezpieczeń, aby określić, jakie zasoby podmiot zabezpieczeń mogą uzyskać dostęp. Zaimplementowanie autoryzacji można użyć zabezpieczeń opartych na rolach .NET Framework.
