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
ms.openlocfilehash: e08cb1b3f4708b4314f0cd663f70fa10aaa1aded
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910686"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Używanie bibliotek pochodzących z częściowo zaufanego kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Ten temat dotyczy zachowania zestawów o silnych nazwach i ma zastosowanie tylko do zestawów [poziomu 1](../../../docs/framework/misc/security-transparent-code-level-1.md) . Silne nazwy nie wpływają na zestawy [poziomu 2](../../../docs/framework/misc/security-transparent-code-level-2.md) w .NET Framework 4 lub nowszym. Aby uzyskać więcej informacji na temat zmian w systemie zabezpieczeń, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Aplikacje, które odbierają mniej niż pełne zaufanie z hosta lub piaskownicy, nie mogą wywoływać udostępnionych bibliotek zarządzanych, chyba że moduł zapisujący biblioteki jawnie zezwala im na <xref:System.Security.AllowPartiallyTrustedCallersAttribute> użycie atrybutu. W związku z tym autorzy aplikacji muszą mieć świadomość, że niektóre biblioteki nie będą dostępne dla nich z częściowo zaufanego kontekstu. Domyślnie cały kod, który jest wykonywany w [piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) z częściowym zaufaniem i nie znajduje się na liście zestawów pełnego zaufania, jest częściowo zaufany. Jeśli nie oczekujesz, że kod będzie wykonywany z częściowo zaufanego kontekstu lub że ma zostać wywołany przez częściowo zaufany kod, nie musisz mieć informacji o informacjach przedstawionych w tej sekcji. Jednak w przypadku pisania kodu, który musi współpracować z częściowo zaufanym kodem lub korzystać z częściowo zaufanego kontekstu, należy wziąć pod uwagę następujące czynniki:  
  
- Biblioteki muszą być podpisane za pomocą silnej nazwy, aby można je było współużytkować przez wiele aplikacji. Silne nazwy umożliwiają umieszczanie kodu w globalnej pamięci podręcznej zestawów lub dodawane do listy pełnych relacji zaufania w trybie piaskownicy <xref:System.AppDomain>oraz umożliwiają klientom sprawdzenie, czy określony element kodu komórkowego rzeczywiście pochodzi od użytkownika.  
  
- Domyślnie biblioteki udostępnione [poziomu 1](../../../docs/framework/misc/security-transparent-code-level-1.md) o silnej nazwie mają niejawny [LinkDemand](../../../docs/framework/misc/link-demands.md) dla pełnego zaufania, bez konieczności wykonywania jakichkolwiek czynności przez moduł zapisujący biblioteki.  
  
- Jeśli obiekt wywołujący nie ma pełnego zaufania, ale nadal próbuje wywołać taką bibliotekę, środowisko uruchomieniowe zgłasza <xref:System.Security.SecurityException> a obiekt wywołujący nie może połączyć się z biblioteką.  
  
- Aby wyłączyć automatyczne **LinkDemand** i zapobiec zgłaszaniu wyjątku, można umieścić atrybut **AllowPartiallyTrustedCallersAttribute** w zakresie zestawu biblioteki udostępnionej. Ten atrybut umożliwia wywoływanie bibliotek z częściowo zaufanego kodu zarządzanego.  
  
- Częściowo zaufany kod, który ma przyznane dostęp do biblioteki z tym atrybutem nadal podlega dalszym ograniczeniom zdefiniowanym <xref:System.AppDomain>przez.  
  
- Nie istnieje programistyczny sposób, aby częściowo zaufany kod wywoływał bibliotekę, która nie ma atrybutu **AllowPartiallyTrustedCallersAttribute** .  
  
 Biblioteki, które są prywatne dla określonej aplikacji, nie wymagają silnej nazwy lub atrybutu **AllowPartiallyTrustedCallersAttribute** i nie mogą odwoływać się do potencjalnie złośliwego kodu poza aplikacją. Taki kod jest chroniony przed zamierzonym lub przypadkowym nadużyciem przez częściowo zaufany kod mobilny bez konieczności wykonywania dodatkowych czynności przez dewelopera.  
  
 Należy rozważyć jawne włączenie korzystania przez częściowo zaufany kod dla następujących typów kodu:  
  
- Kod, który został pracujemy testowany pod kątem luk w zabezpieczeniach i jest zgodny z wytycznymi opisanymi w temacie [zasady bezpiecznego kodowania](../../standard/security/secure-coding-guidelines.md).  
  
- Biblioteki kodu o silnej nazwie, które są przeznaczone dla częściowo zaufanych scenariuszy.  
  
- Wszystkie składniki (częściowo lub w pełni zaufane) podpisane przy użyciu silnej nazwy, które będą wywoływane przez kod pobrany z Internetu.  
  
> [!NOTE]
> Niektóre klasy w bibliotece klas .NET Framework nie mają atrybutu **AllowPartiallyTrustedCallersAttribute** i nie mogą być wywoływane przez częściowo zaufany kod.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
