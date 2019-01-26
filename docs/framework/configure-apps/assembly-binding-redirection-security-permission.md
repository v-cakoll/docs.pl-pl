---
title: Uprawnienie zabezpieczeń przekierowania powiązania zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: 25b74de66fbf053b4d9129ab6ca0bef1530bf228
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083759"
---
# <a name="assembly-binding-redirection-security-permission"></a>Uprawnienie zabezpieczeń przekierowania powiązania zestawu
Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń. Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich. To uprawnienie jest przydzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagą <xref:System.Security.Permissions.SecurityPermission>. Zestawy zarządzane nie mają uprawnień domyślnie.  
  
 Do aplikacji działających w strefie intranetu i zaufane (maszyna lokalna) jest udzielane uprawnienie zabezpieczeń. Aplikacje działające w strefie Internet jest bezwzględnie zabronione wykonywaniu przekierowanie powiązań zestawów.  
  
 Uprawnienie nie jest wymagane, jeśli przekierowanie zestawów jest wykonywana w plik zasad wydawcy, który jest kontrolowany przez wydawcę składnika lub w pliku konfiguracji komputera, który jest kontrolowany przez administratora. Jednak uprawnienia są wymagane dla aplikacji, aby jawnie Ignoruj przy użyciu zasad wydawcy [ \<zastosować publisherPolicy = "no" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracyjnym aplikacji.  
  
 W poniższej tabeli przedstawiono domyślne ustawienia zabezpieczeń dla **BindingRedirects** flagi.  
  
|Strefy|Ustawienia flagi BindingRedirects|  
|----------|-----------------------------------|  
|Zaufanej strefy (komputer lokalny)|**DALEJ**|  
|Strefy intranet|**DALEJ**|  
|Strefa Internet|**OFF**|  
|Niezaufane stref|**OFF**|  
  
 Administrator może zmienić te ustawienia zabezpieczeń do obsługi lub ograniczyć konkretnych scenariuszy na danym komputerze. Są dostępne żadne narzędzia wielokanałowej **BindingRedirects** ustawienia domyślnego; flagi administrator musi ręcznie edytować plik Security.config — na komputerze użytkownika.  
  
## <a name="see-also"></a>Zobacz także
- [Pliki zasad wydawcy i wykonywanie Side-by-Side](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)
- [Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [Wykonywanie równoczesne](../../../docs/framework/deployment/side-by-side-execution.md)
