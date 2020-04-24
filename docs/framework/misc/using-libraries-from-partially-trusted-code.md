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
ms.openlocfilehash: 61291a07639c3f92a05f78dff49f6b20f1aee77e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645717"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Używanie bibliotek pochodzących z częściowo zaufanego kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Ten temat dotyczy zachowania zestawów o silnych nazwach i dotyczy tylko zestawów [poziomu 1.](security-transparent-code-level-1.md) [Security-Transparent Code, zestawy poziomu 2](security-transparent-code-level-2.md) w .NET Framework 4 lub nowszych nie są zagrożone przez silne nazwy. Aby uzyskać więcej informacji na temat zmian w systemie zabezpieczeń, zobacz [Zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Aplikacje, które otrzymują mniej niż pełne zaufanie od hosta lub piaskownicy nie mogą wywoływać udostępnionych bibliotek <xref:System.Security.AllowPartiallyTrustedCallersAttribute> zarządzanych, chyba że moduł zapisujący bibliotekę zezwala im na korzystanie z atrybutu. W związku z tym autorzy aplikacji muszą być świadomi, że niektóre biblioteki nie będą dostępne dla nich z częściowo zaufanego kontekstu. Domyślnie cały kod, który jest wykonywany w [obszarze izolowanym](how-to-run-partially-trusted-code-in-a-sandbox.md) częściowego zaufania i nie znajduje się na liście zestawów pełnego zaufania jest częściowo zaufany. Jeśli nie oczekujesz, że kod ma być wykonywany z częściowo zaufanego kontekstu lub wywoływany przez częściowo zaufany kod, nie musisz się martwić o informacje zawarte w tej sekcji. Jednak jeśli piszesz kod, który musi wchodzić w interakcje z częściowo zaufanym kodem lub działać z częściowo zaufanego kontekstu, należy wziąć pod uwagę następujące czynniki:  
  
- Biblioteki muszą być podpisane przy użyciu silnej nazwy, aby były współużytkowane przez wiele aplikacji. Silne nazwy umożliwiają umieszczenie kodu w globalnej pamięci podręcznej zestawów lub do <xref:System.AppDomain>listy pełnego zaufania piaskownicy i umożliwiają konsumentom sprawdzenie, czy określony fragment kodu mobilnego faktycznie pochodzi od Ciebie.  
  
- Domyślnie biblioteki udostępnione [poziomu 1](security-transparent-code-level-1.md) o silnej nazwie automatycznie wykonują niejawne [linkdemand](link-demands.md) dla pełnego zaufania, bez konieczności wykonywania cokolwiek przez moduł zapisujący bibliotekę.  
  
- Jeśli obiektu wywołującego nie ma pełnego zaufania, ale nadal próbuje wywołać <xref:System.Security.SecurityException> taką bibliotekę, środowisko wykonawcze zgłasza a i obiektu wywołującego nie może połączyć się z biblioteką.  
  
- Aby wyłączyć automatyczne **LinkDemand** i zapobiec wyjątek, można umieścić **AllowPartiallyTrustedCallersAttribute** atrybut w zakresie zestawu biblioteki udostępnionej. Ten atrybut umożliwia biblioteki, które mają być wywoływane z częściowo zaufanego kodu zarządzanego.  
  
- Częściowo zaufany kod, który jest przyznawany dostęp do biblioteki z tym atrybutem nadal podlega dalszym ograniczeniom zdefiniowanym <xref:System.AppDomain>przez .  
  
- Nie ma programowego sposobu częściowo zaufanego kodu do wywołania biblioteki, która nie ma **atrybutu AllowPartiallyTrustedCallersAttribute.**  
  
 Biblioteki, które są prywatne dla określonej aplikacji nie wymagają silnej nazwy lub **AllowPartiallyTrustedCallersAttribute** atrybut i nie można odwoływać się przez potencjalnie złośliwy kod poza aplikacją. Taki kod jest chroniony przed zamierzonym lub niezamierzonym niewłaściwym użyciem przez częściowo zaufany kod mobilny bez konieczności wykonywania przez dewelopera żadnych dodatkowych działań.  
  
 Należy rozważyć jawnie włączenie użycia przez częściowo zaufany kod dla następujących typów kodu:  
  
- Kod, który został pilnie przetestowany pod kątem luk w zabezpieczeniach i jest zgodny z wytycznymi opisanymi w [wskazówki dotyczące bezpiecznego kodowania.](../../standard/security/secure-coding-guidelines.md)  
  
- Biblioteki kodu o silnej nazwie, które są specjalnie napisane dla częściowo zaufanych scenariuszy.  
  
- Wszystkie składniki (częściowo lub w pełni zaufane) podpisane przy silnym nazwiskiem, które będą wywoływane przez kod pobrany z Internetu.  
  
> [!NOTE]
> Niektóre klasy w bibliotece klas .NET Framework nie mają atrybutu **AllowPartiallyTrustedCallersAttribute** i nie można ich wywołać za pomocą częściowo zaufanego kodu.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia dostępu kodu](code-access-security.md)
