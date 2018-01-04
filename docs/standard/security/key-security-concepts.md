---
title: "Główne pojęcia dotyczące zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8e11e22d98954d9656357e11fbb4ca94ad673659
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="key-security-concepts"></a>Główne pojęcia dotyczące zabezpieczeń
Microsoft .NET Framework zapewnia oparte na rolach zabezpieczeń mających na celu adres problemy z zabezpieczeniami dotyczące kodu przenośnego i zapewnienie obsługi, który umożliwia ustalenie, użytkownicy są upoważnione na.  
  
## <a name="type-safety-and-security"></a>Typ bezpieczeństwa i zabezpieczeń  
 Bezpieczny kod uzyskuje dostęp do lokalizacji pamięci, który jest upoważniony do dostępu. (Dla tej dyskusji zabezpieczeń w szczególności odwołuje się do pamięci typu bezpieczeństwa i nie należy mylić z typu bezpieczeństwa w szerszym zakresie.) Na przykład bezpieczny kod nie można odczytać wartości z pól prywatnych innego obiektu. Uzyskuje dostęp do typów tylko w sposób wyraźnie określone, dozwolony.  
  
 Podczas just in time (JIT) kompilacji proces weryfikacji opcjonalne sprawdza, czy metadane i języku pośrednim firmy Microsoft (MSIL) z metodę, aby skompilować JIT do kodu macierzystego maszyny, aby sprawdzić, czy są one bezpieczne typu. Ten proces jest pomijane, jeśli kod ma uprawnienie do pominięcia weryfikacji. Aby uzyskać więcej informacji o weryfikacji, zobacz [proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md).  
  
 Weryfikacji zabezpieczeń nie jest wymagane do uruchomienia kodu zarządzanego, bezpieczeństwo typów odgrywa kluczową role w zestawie izolacji i wymuszanie zabezpieczeń. Jeśli kod jest typu bezpieczne, środowisko uruchomieniowe języka wspólnego całkowicie można odizolować zestawy od siebie. Izolacja gwarantuje, że zestawy nie może mieć niekorzystny wpływ na siebie i zwiększa niezawodność aplikacji. Bezpieczne składniki mogą wykonywać bezpiecznie w ramach tego samego procesu, nawet jeśli są zaufane na różnych poziomach. Gdy kodu nie jest typem bezpieczne, może wystąpić niepożądane skutki uboczne. Na przykład środowisko uruchomieniowe nie mogą uniemożliwiać kodu zarządzanego z wywołania do kodu macierzystego (niezarządzany) i wykonywanie operacji złośliwe. Jeśli kod jest typu bezpieczne, mechanizmu wymuszania zabezpieczeń środowiska uruchomieniowego zapewnia że go nie dostęp do kodu macierzystego, chyba że ma uprawnienia. Cały kod, który nie jest typem bezpieczne musi mieć przyznaną <xref:System.Security.Permissions.SecurityPermission> z elementu członkowskiego wyliczenia przekazany <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> do uruchomienia.  
  
 Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Główne  
 Podmiot zabezpieczeń reprezentuje tożsamość i rolę użytkownika i działa w imieniu użytkownika. Zabezpieczenia oparte na rolach w programie .NET Framework obsługuje trzy rodzaje podmiotów zabezpieczeń:  
  
-   Ogólny podmiotów reprezentują użytkowników i role, które istnieją niezależnie od użytkowników systemu Windows i ról.  
  
-   Podmioty zabezpieczeń systemu Windows reprezentują użytkowników systemu Windows i ich role (lub ich grupy systemu Windows). Podmiot zabezpieczeń systemu Windows mogą personifikować innego użytkownika, co oznacza, że podmiot zabezpieczeń może dostępu do zasobu w imieniu użytkownika podczas przedstawiania tożsamości, która należy do tego użytkownika.  
  
-   Niestandardowe podmiotów zabezpieczeń mogą zostać zdefiniowane przez aplikację w dowolny sposób, który jest wymagany dla tej konkretnej aplikacji. Można rozszerzają podstawowe pojęcie tożsamości podmiotu i ról.  
  
 Aby uzyskać więcej informacji, zobacz [podmiot zabezpieczeń i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Uwierzytelnianie  
 Uwierzytelnianie to proces odnajdywania i weryfikowania tożsamości podmiot zabezpieczeń, sprawdzając poświadczenia użytkownika i sprawdzanie poprawności poświadczeń dla niektórych urzędu. Dane uzyskane podczas uwierzytelniania jest użyteczne bezpośrednio w kodzie. Umożliwia także zabezpieczenia oparte na rolach .NET Framework uwierzytelnić bieżącego użytkownika i określenia, czy zezwalać tego podmiotu zabezpieczeń dostępu kodu do. Zobacz przeciążeń <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> metody przykłady tego, jak uwierzytelniać podmiot zabezpieczeń dla określonych ról. Na przykład można użyć <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> przeciążenia, aby określić, czy bieżący użytkownik jest członkiem grupy Administratorzy.  
  
 Różnych mechanizmów uwierzytelniania używanych dzisiaj, z których wiele może być używany z zabezpieczeń opartych na rolach .NET Framework. Niektóre z najczęściej używane mechanizmów są podstawowe, szyfrowane, Passport, system operacyjny (na przykład protokołu NTLM lub Kerberos) lub mechanizmów zdefiniowanym przez aplikację.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wymaga aktywny podmiot zabezpieczeń administratora. `name` Parametr jest `null`, dzięki czemu każdy użytkownik, który jest administratorem, aby przekazać żądanie.  
  
> [!NOTE]
>  W systemie Windows Vista kontroli konta użytkownika (UAC) określa uprawnienia użytkownika. Jeśli jesteś członkiem wbudowanej grupy Administratorzy, masz przypisane dwa tokeny dostępu w czasie wykonywania: token dostępu użytkownika standardowego i token dostępu administratora. Domyślnie jesteś w roli użytkownika standardowego. Do wykonania kodu, musisz być administratorem, musi najpierw podwyższenie Twoje uprawnienia od użytkownika standardowego do administratora. Można to zrobić, podczas uruchamiania aplikacji przez kliknięcie prawym przyciskiem myszy ikonę aplikacji i wskazujący, że chcesz uruchomić jako administrator.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 W poniższym przykładzie pokazano sposób określania tożsamości podmiotu zabezpieczeń i dostępne do principal role. Aplikacja, w tym przykładzie może być aby upewnić się, że bieżący użytkownik jest w roli, możesz zezwolić na korzystanie z aplikacji.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autoryzacja  
 Autoryzacja jest proces określania, czy podmiot zabezpieczeń może wykonać żądanej akcji. Występuje po uwierzytelnieniu i używa informacji o tożsamości podmiotu i ról do ustalenia podmiot zabezpieczeń mogą uzyskiwać dostęp do zasobów. Zabezpieczenia oparte na rolach .NET Framework służy do implementowania autoryzacji.
