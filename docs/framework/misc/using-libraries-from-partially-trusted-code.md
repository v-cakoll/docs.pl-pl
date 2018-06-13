---
title: Używanie bibliotek pochodzących z częściowo zaufanego kodu
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b2eaf6ccebed38c778e328e34cb6f53177347b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397663"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Używanie bibliotek pochodzących z częściowo zaufanego kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Ten temat dotyczy zachowanie zestawy o silnych nazwach i ma zastosowanie tylko do [poziom 1](../../../docs/framework/misc/security-transparent-code-level-1.md) zestawów. [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md) zestawów w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] lub później nie dotyczy silnej nazwy. Aby uzyskać więcej informacji na temat zmian w systemie zabezpieczeń, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Aplikacje odbierające mniej niż pełne zaufanie od ich hosta lub piaskownicy nie mogą wywoływać udostępnionego zarządzane bibliotek, chyba, że moduł zapisujący biblioteki w szczególności pozwala na ich za pośrednictwem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu. W związku z tym zapisywania aplikacji należy pamiętać, że niektóre biblioteki nie będą dostępne do nich z kontekstu częściowo zaufany. Domyślnie, całego kodu, który jest wykonywany w częściowo zaufanym [piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) i nie znajduje się w listę zestawów pełnego zaufania jest częściowo zaufany. Jeśli nie będzie można wykonać z kontekstu częściowo zaufany lub jest wywoływany przez kod częściowo zaufany kod, nie trzeba być zajmującym się z informacjami w tej sekcji. Jednak podczas pisania kodu, który musi współdziałać z częściowo zaufanego kodu lub nie działać w kontekście częściowo zaufany, należy rozważyć następujące czynniki:  
  
-   Biblioteki muszą być podpisane przy użyciu silnej nazwy, aby być współużytkowane przez wiele aplikacji. Silne nazwy Zezwalaj swój kod, aby być umieszczone w globalnej pamięci podręcznej zestawów lub dodane do listy pełnego zaufania sandboxing <xref:System.AppDomain>, i konsumentów sprawdzić, czy z określonym wystąpieniem dostępu mobilnego faktycznie pochodzi z możesz zezwolić.  
  
-   Domyślnie o silnych nazwach [poziom 1](../../../docs/framework/misc/security-transparent-code-level-1.md) współużytkowanych bibliotekach wykonać niejawnej [LinkDemand](../../../docs/framework/misc/link-demands.md) dla pełnego zaufania automatycznie, bez zapisywania biblioteki konieczności wykonywania żadnych czynności.  
  
-   Jeśli obiekt wywołujący nie ma pełnego zaufania, ale nadal próba wywołania takie biblioteki, środowisko uruchomieniowe zgłasza <xref:System.Security.SecurityException> i obiekt wywołujący nie może połączyć do biblioteki.  
  
-   Aby wyłączyć automatyczne **LinkDemand** i zapobiec z został zgłoszony wyjątek, możesz umieścić **AllowPartiallyTrustedCallersAttribute** atrybut na zakres zestaw udostępnionego Biblioteka. Ten atrybut umożliwia bibliotek ma być wywoływana z częściowo zaufanego kodu zarządzanego.  
  
-   Częściowo zaufany kod, który uzyskuje dostęp do biblioteki z tym atrybutem jest nadal może ulec dodatkowe ograniczenia zdefiniowane przez <xref:System.AppDomain>.  
  
-   Nie istnieje sposób programowy dla częściowo zaufanego kodu do wywoływania biblioteki, która nie ma **AllowPartiallyTrustedCallersAttribute** atrybutu.  
  
 Biblioteki, w których są prywatne do konkretnej aplikacji nie wymagają silnej nazwy lub **AllowPartiallyTrustedCallersAttribute** atrybutu i nie może odwoływać się potencjalnie złośliwy kod z aplikacji. Taki kod jest chroniony przed niewłaściwym użyciem zamierzone lub przypadkowe częściowo zaufany kod przenośnych bez developer konieczności wykonywania żadnych dodatkowych działań.  
  
 Należy rozważyć jawne włączenie używany przez kod częściowo zaufany dla następujących typów kodu:  
  
-   Kod, który dokładnie przetestowano dla luk w zabezpieczeniach i jest zgodne z wytycznymi opisanego w [Secure wytyczne kodowania](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Biblioteki kodów o silnej nazwie, napisanych specjalnie dla scenariuszy częściowo zaufany.  
  
-   Wszystkie składniki (czy częściowo lub całkowicie zaufane) podpisany silną nazwą, która zostanie wywołana przez kod, który jest pobierany z Internetu.  
  
> [!NOTE]
>  Nie masz niektórych klas w bibliotece klas programu .NET Framework **AllowPartiallyTrustedCallersAttribute** atrybutu i nie może być wywoływana przez kod częściowo zaufany.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
