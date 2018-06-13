---
title: Uprawnienie zabezpieczeń przekierowania powiązania zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ef9295028aeb7bfcc6df88e9c8bb7f80e2a31368
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743267"
---
# <a name="assembly-binding-redirection-security-permission"></a>Uprawnienie zabezpieczeń przekierowania powiązania zestawu
Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń. Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich. Uprawnienie zostanie udzielone przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> Flaga na <xref:System.Security.Permissions.SecurityPermission>. Zarządzanych zestawów nie mają uprawnień domyślnie.  
  
 Uprawnienie zabezpieczeń otrzymuje do aplikacji działających w strefie intranetu i zaufane (komputer lokalny). Aplikacje uruchomione w strefie Internet są zabronione wykonywanie przekierowanie powiązań zestawów.  
  
 Uprawnienie nie jest wymagane, jeśli przekierowanie zestawów odbywa się w pliku zasad wydawcy, który jest kontrolowany przez wydawcę składnika lub w pliku konfiguracji komputera, które są kontrolowane przez administratora. Jednak uprawnienia są wymagane dla aplikacji, aby jawnie Ignoruj przy użyciu zasad wydawcy [ \<zastosować publisherPolicy = "nie" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracyjnym aplikacji.  
  
 W poniższej tabeli przedstawiono domyślne ustawienia zabezpieczeń dla **BindingRedirects** flagi.  
  
|strefy|Ustawienia flagi BindingRedirects|  
|----------|-----------------------------------|  
|Strefa Zaufane (komputer lokalny)|**ON**|  
|Strefy intranet|**ON**|  
|Strefa Internet|**OFF**|  
|Niezaufane stref|**OFF**|  
  
 Administrator może zmienić te ustawienia zabezpieczeń do obsługi lub ograniczyć określonych scenariuszy na danym komputerze. Nie ma żadnych narzędzi do zmiany **BindingRedirects** ustawienia domyślnego; flagi administrator musi ręcznie zmodyfikować plik Security.config — na komputerze użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasad wydawcy i wykonywanie Side-by-Side](http://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [Wykonywanie równoczesne](../../../docs/framework/deployment/side-by-side-execution.md)
