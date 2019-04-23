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
ms.openlocfilehash: 7a3bbbaa565a6c118082456a1ab6d7af59db7067
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119278"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Używanie bibliotek pochodzących z częściowo zaufanego kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  W tym temacie adresy zachowanie zestawy o silnych nazwach i ma zastosowanie tylko do [poziomu 1](../../../docs/framework/misc/security-transparent-code-level-1.md) zestawów. [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md) zestawów w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] lub nowszej nie dotyczy silne nazwy. Aby uzyskać więcej informacji na temat zmian w systemie zabezpieczeń, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Aplikacje odbierające mniejsza niż pełne zaufanie od hosta lub piaskownicy nie są dozwolone do wywołania udostępnionego zarządzanych bibliotek, chyba że moduł zapisujący biblioteki specjalnie pozwala na ich za pośrednictwem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu. W związku z tym autorzy aplikacji należy pamiętać, że niektóre biblioteki nie będą dostępne do nich z częściowo zaufanych kontekstu. Domyślnie, cały kod, który wykonuje w częściowym zaufaniu [piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) i nie znajduje się w listy zestawów pełnego zaufania jest częściowo zaufany. Jeśli nie powinien być wykonywany z częściowo zaufanych kontekstu lub być wywoływany przez kod częściowo zaufany kod, masz nie trzeba się troszczyć o informacje przedstawione w tej sekcji. Jednak jeśli piszesz kod, który musi współdziałać z częściowo zaufanego kodu lub nie działać z częściowo zaufanych kontekstu, należy rozważyć następujące czynniki:  
  
-   Biblioteki musi być podpisany silną nazwą, aby być współużytkowane przez wiele aplikacji. Silne nazwy Zezwalaj kodu mają być umieszczone w globalnej pamięci podręcznej lub dodać do listy pełnego zaufania piaskownicy <xref:System.AppDomain>, i pozwala użytkownikom sprawdzić, czy określonego fragmentu kodu mobilnego rzeczywiście pochodzi ze strony użytkownika.  
  
-   Domyślnie o silnej nazwie [poziomu 1](../../../docs/framework/misc/security-transparent-code-level-1.md) biblioteki udostępnione wykonać ukrytego [LinkDemand](../../../docs/framework/misc/link-demands.md) dla pełnego zaufania automatycznie, bez zapisywania biblioteki potrzeby podejmować żadnych działań.  
  
-   Jeśli obiekt wywołujący nie jest w pełni zaufany, ale nadal próbuje wywołać takie biblioteki, środowisko wykonawcze zgłasza <xref:System.Security.SecurityException> i element wywołujący nie ma zezwolenia na łącze do biblioteki.  
  
-   Aby wyłączyć automatyczne **LinkDemand** i zapobiec wyjątek z jest zgłaszana, możesz umieścić **AllowPartiallyTrustedCallersAttribute** atrybutu w zakresie zestaw wspólny Biblioteka. Ten atrybut umożliwia bibliotek do wywołania z częściowo zaufanego kodu zarządzanego.  
  
-   Częściowo zaufany kod, który uzyskuje dostęp do biblioteki, z tym atrybutem jest nadal podlega procesowi dodatkowe ograniczenia zdefiniowane przez <xref:System.AppDomain>.  
  
-   Nie istnieje sposób programistyczny dla częściowo zaufanego kodu w celu wywołania biblioteki, która nie ma **AllowPartiallyTrustedCallersAttribute** atrybutu.  
  
 Bibliotek, które są prywatne z określoną aplikacją nie wymagają silnej nazwy lub **AllowPartiallyTrustedCallersAttribute** atrybutu i nie może być przywoływany przez potencjalnie złośliwy kod poza aplikacją. Taki kod jest chronione przed zamierzone lub przypadkowe nadużycie przez częściowo zaufany kod przenośny bez deweloper musi wykonywać żadnych dodatkowych czynności.  
  
 Należy rozważyć jawne włączenie użycia przez częściowo zaufany kod dla następujących typów kodu:  
  
-   Kod, który był testowany przerwami dla luki w zabezpieczeniach i jest zgodne z wytycznymi opisany w [Secure wytycznych kodowania](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Bibliotek o silnej nazwie do kodu, które są opracowane specjalnie dla scenariuszy częściowo zaufany.  
  
-   Wszystkie składniki (czy częściowo lub całkowicie zaufanych) podpisany silną nazwą, która zostanie wywołana przez kod, który jest pobierany z Internetu.  
  
> [!NOTE]
>  Niektóre klasy w bibliotece klas programu .NET Framework nie posiadają **AllowPartiallyTrustedCallersAttribute** atrybutu i nie może być wywoływany przez częściowo zaufany kod.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
