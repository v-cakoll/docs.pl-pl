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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705975"
---
# <a name="key-security-concepts"></a>Główne pojęcia dotyczące zabezpieczeń
Microsoft .NET Framework oferuje zabezpieczenia oparte na rolach, które ułatwiają rozwiązywanie problemów związanych z bezpieczeństwem kodu mobilnego i zapewnianie pomocy technicznej umożliwiającej składnikom określenie, które użytkownicy mają uprawnienia do wykonywania.  
  
## <a name="type-safety-and-security"></a>Bezpieczeństwo i zabezpieczenia typów  
 Kod bezpieczny dla typu uzyskuje dostęp tylko do lokalizacji pamięci, do której ma dostęp. (W przypadku tej dyskusji zabezpieczenia typu w odniesieniu do ochrony typu pamięci nie należy mylić z bezpieczeństwem typu w szerszym zakresie). Na przykład kod bezpieczny dla typu nie może odczytywać wartości z prywatnych pól innego obiektu. Uzyskuje dostęp do typów tylko w dobrze zdefiniowanych, dozwolony sposób.  
  
 Podczas kompilacji just-in-Time (JIT) opcjonalny proces weryfikacji sprawdza metadane i języka pośredniego firmy Microsoft (MSIL) metody, aby były kompilowane JIT w kodzie macierzystym, aby sprawdzić, czy są one bezpieczne. Ten proces jest pomijany, jeśli kod ma uprawnienia do pomijania weryfikacji. Aby uzyskać więcej informacji na temat weryfikacji, zobacz [proces wykonywania zarządzanego](../../../docs/standard/managed-execution-process.md).  
  
 Mimo że weryfikacja typu zabezpieczenia nie jest obowiązkowa do uruchamiania kodu zarządzanego, bezpieczeństwo typu odgrywa kluczową rolę w zakresie izolacji zestawów i wymuszania zabezpieczeń. Gdy kod jest bezpiecznym typem, środowisko uruchomieniowe języka wspólnego może całkowicie izolować zestawy od siebie. Ta izolacja pomaga upewnić się, że zestawy nie mogą niekorzystnie wpływać na siebie i zwiększa niezawodność aplikacji. Składniki bezpieczne dla typów mogą być wykonywane bezpiecznie w tym samym procesie, nawet jeśli są one zaufane na różnych poziomach. Gdy kod nie jest bezpiecznym typem, mogą wystąpić niepożądane skutki uboczne. Na przykład środowisko uruchomieniowe nie może zapobiec wywołaniu kodu natywnego (niezarządzanego) i wykonywaniu złośliwych operacji. Gdy kod jest bezpieczny, mechanizm wymuszania zabezpieczeń środowiska uruchomieniowego zapewnia, że nie uzyskuje dostępu do kodu natywnego, chyba że ma odpowiednie uprawnienia. W przypadku wszystkich typów, które nie są bezpieczne, należy przyznać <xref:System.Security.Permissions.SecurityPermission> z przekazaną <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> członkowskim wyliczenia do uruchomienia.  
  
 Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Główne  
 Podmiot zabezpieczeń reprezentuje tożsamość i rolę użytkownika oraz działa w imieniu użytkownika. Zabezpieczenia oparte na rolach w .NET Framework obsługują trzy rodzaje podmiotów głównych:  
  
- Ogólne podmioty zabezpieczeń reprezentują użytkowników i role, które istnieją niezależnie od użytkowników i ról systemu Windows.  
  
- Główne systemy Windows reprezentują użytkowników systemu Windows i ich role (lub ich grupy systemu Windows). Podmiot zabezpieczeń systemu Windows może personifikować innego użytkownika, co oznacza, że podmiot zabezpieczeń może uzyskać dostęp do zasobu w imieniu użytkownika podczas prezentowania tożsamości należącej do danego użytkownika.  
  
- Niestandardowe podmioty zabezpieczeń mogą być definiowane przez aplikację w dowolny sposób, który jest wymagany dla danej aplikacji. Mogą one stanowić podstawowe pojęcie tożsamości i ról podmiotu zabezpieczeń.  
  
 Aby uzyskać więcej informacji, zobacz [obiekty główne i tożsamości](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Uwierzytelnianie  
 Uwierzytelnianie to proces odnajdywania i weryfikowania tożsamości podmiotu zabezpieczeń, sprawdzając poświadczenia użytkownika i sprawdzając poświadczenia dla niektórych urzędów. Informacje uzyskane podczas uwierzytelniania są bezpośrednio użyteczne w kodzie. Możesz również użyć .NET Framework zabezpieczenia oparte na rolach, aby uwierzytelnić bieżącego użytkownika i określić, czy zezwolić podmiotowi zabezpieczeń na dostęp do kodu. Zobacz przeciążanie metody <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType>, aby zapoznać się z przykładami sposobu uwierzytelniania podmiotu zabezpieczeń dla określonych ról. Można na przykład użyć przeciążenia <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType>, aby określić, czy bieżący użytkownik jest członkiem grupy Administratorzy.  
  
 Obecnie używane są różne mechanizmy uwierzytelniania, z których wiele można korzystać w ramach zabezpieczeń opartych na rolach .NET Framework. Najczęściej używanymi mechanizmami są podstawowe, szyfrowane, paszporty, system operacyjny (na przykład NTLM lub Kerberos) lub mechanizmy zdefiniowane przez aplikację.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wymaga, aby aktywny podmiot zabezpieczeń był administratorem. `name` parametr jest `null`, co umożliwia każdemu użytkownikowi, który jest administratorem, przekazanie żądania.  
  
> [!NOTE]
> W systemie Windows Vista Kontrola konta użytkownika (UAC) określa uprawnienia użytkownika. Jeśli jesteś członkiem wbudowanej grupy Administratorzy, masz przypisane dwa tokeny dostępu w czasie wykonywania: token dostępu użytkownika standardowego i token dostępu administratora. Domyślnie jesteś w roli użytkownika standardowego. Aby wykonać kod wymagający administratora, należy najpierw podnieść poziom uprawnień użytkownika standardowego do administratora. Można to zrobić podczas uruchamiania aplikacji przez kliknięcie prawym przyciskiem myszy ikony aplikacji i wskazanie, że chcesz uruchomić program jako administrator.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 W poniższym przykładzie pokazano, jak określić tożsamość podmiotu zabezpieczeń i role dostępne dla podmiotu zabezpieczeń. W przypadku aplikacji tego przykładu można potwierdzić, że bieżący użytkownik znajduje się w roli, którą zezwolisz na korzystanie z aplikacji.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autoryzacja  
 Autoryzacja to proces ustalania, czy podmiot zabezpieczeń może wykonać żądaną akcję. Autoryzacja jest wykonywana po uwierzytelnieniu i używa informacji o tożsamości i rolach podmiotu zabezpieczeń w celu określenia zasobów, do których podmiot zabezpieczeń może uzyskać dostęp. Aby zaimplementować autoryzację, można użyć zabezpieczeń opartych na rolach .NET Framework.
