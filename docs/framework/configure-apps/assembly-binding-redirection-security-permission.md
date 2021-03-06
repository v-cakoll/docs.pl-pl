---
title: Uprawnienie zabezpieczeń przekierowania powiązania zestawu
description: Dowiedz się więcej o uprawnieniach zabezpieczeń wymaganych do jawnego przekierowania powiązania zestawu w pliku konfiguracyjnym aplikacji w programie .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: a8596bcac4efb0aea07efcfde6726d8bbf148c24
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105096"
---
# <a name="assembly-binding-redirection-security-permission"></a>Uprawnienie zabezpieczeń przekierowania powiązania zestawu
Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń. Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich. Uprawnienie jest udzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagi na <xref:System.Security.Permissions.SecurityPermission> . Zarządzane zestawy nie mają domyślnie żadnych uprawnień.  
  
 Uprawnienia zabezpieczeń są udzielane aplikacjom działającym w strefie zaufanej (komputer lokalny) i intranet. Aplikacje działające w strefie Internetu są ściśle zabronione przed przekierowaniem powiązań zestawu.  
  
 Uprawnienie nie jest wymagane, jeśli przekierowanie zestawu jest wykonywane w pliku zasad wydawcy, który jest kontrolowany przez wydawcę składnika lub w pliku konfiguracyjnym komputera kontrolowanym przez administratora. Jednak uprawnienie jest wymagane, aby aplikacja jawnie ignorował zasady wydawcy przy użyciu [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracji aplikacji.  
  
 W poniższej tabeli przedstawiono domyślne ustawienia zabezpieczeń flagi **BindingRedirects** .  
  
|Strefa|Ustawienie flagi BindingRedirects|  
|----------|-----------------------------------|  
|Strefa zaufana (maszyna lokalna)|**Z**|  
|Strefa intranetowa|**Z**|  
|Strefa Internet|**Logowanie**|  
|Niezaufane strefy|**Logowanie**|  
  
 Administrator może zmienić te ustawienia zabezpieczeń, aby obsługiwać lub ograniczać określone scenariusze na danym komputerze. Nie ma narzędzi do zmiany ustawienia flagi **BindingRedirects** z domyślnego. Administrator musi ręcznie edytować plik Security.config na komputerze użytkownika.  
  
## <a name="see-also"></a>Zobacz też

- [Pliki zasad wydawcy i wykonywanie równoczesne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań](how-to-enable-and-disable-automatic-binding-redirection.md)
- [Wykonywanie równoczesne](../deployment/side-by-side-execution.md)
