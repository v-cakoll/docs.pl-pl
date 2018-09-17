---
title: 'Porady: włączanie i wyłączanie automatycznego przekierowania powiązań'
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cf38bd753127e40c61512411c7aa2ebbbd7687db
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746929"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Porady: włączanie i wyłączanie automatycznego przekierowania powiązań

Podczas kompilowania aplikacji w programie Visual Studio, których platformą docelową [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] i nowsze wersje, przekierowania powiązań mogą być automatycznie dodawane do pliku konfiguracyjnego aplikacji w celu zastąpienia ujednolicenia zestawów. Przekierowania powiązań są dodawane, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu, nawet jeśli przekierowania powiązań zostaną określone ręcznie w pliku konfiguracji aplikacji. Funkcja automatycznego przekierowywania powiązań dotyczy tradycyjnych aplikacji komputerowych i aplikacji sieci web, których platformą docelową [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] lub nowszej, chociaż zachowanie jest nieco inne w przypadku aplikacji sieci web. Można włączyć automatyczne przekierowywanie połączeń, jeśli są używane aplikacje, których platformami docelowymi są poprzednie wersje programu .NET Framework, ale można też wyłączyć tę funkcję, aby używać tworzonych ręcznie przekierowań powiązań.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Wyłączyć automatyczne przekierowywanie powiązań w aplikacjach klasycznych

Automatyczne przekierowania powiązań są domyślnie włączone dla tradycyjnych aplikacji komputerowych, których platformą docelową [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] i nowszych wersjach. Przekierowania powiązań są dodawane do wyjściowego pliku konfiguracji (app.config), gdy aplikacja jest kompilowana, co powoduje zastąpienie ujednolicenia zestawów, które mogłoby mieć miejsce. Źródłowy plik app.config nie jest modyfikowany. Tę funkcję można wyłączyć, modyfikując plik projektu dla aplikacji.

1. Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:

   - W programie Visual Studio wybierz projekt w **Eksploratora rozwiązań**, a następnie wybierz **Otwórz Folder w Eksploratorze plików** z menu skrótów. W Eksploratorze plików Znajdź plik projektu (.csproj lub .vbproj), a następnie otwórz go w Notatniku.
   - W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**. Ponownie kliknij prawym przyciskiem myszy zwolnionego projektu, a następnie wybierz **Edytuj [projectname.csproj]**.

2. W pliku projektu znajdź następujący wpis właściwości:

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Zmiana `true` do `false`:

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Ręcznie Włącz automatyczne przekierowania powiązań

Automatyczne przekierowania powiązań w istniejących aplikacjach można włączyć w tym docelowymi są starsze wersje programu .NET Framework lub w przypadkach, gdy zostanie wyświetlony automatycznie monit dodane przekierowanie. Jeśli elementem docelowym nowszą wersję platformy, ale nie są wyświetlane automatycznie monity można dodać przekierowania, prawdopodobnie otrzymasz dane wyjściowe kompilacji, który sugeruje, że należy ponownie zamapować zestawów.

1. Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:

   - W programie Visual Studio wybierz projekt w **Eksploratora rozwiązań**, a następnie wybierz **Otwórz Folder w Eksploratorze plików** z menu skrótów. W Eksploratorze plików Znajdź plik projektu (.csproj lub .vbproj), a następnie otwórz go w Notatniku.
   - W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**. Ponownie kliknij prawym przyciskiem myszy zwolnionego projektu, a następnie wybierz **Edytuj [projectname.csproj]**.

2. Dodaj następujący element do pierwszej grupy właściwości konfiguracji (w obszarze \<PropertyGroup > tag):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   Poniżej przedstawiono przykładowy plik projektu z elementem wstawione:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. Skompiluj aplikację.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Włącz automatyczne przekierowania powiązań w aplikacjach sieci web

Automatyczne przekierowania powiązań są w przypadku aplikacji internetowych implementowane w inny sposób. Ponieważ źródłowy plik konfiguracji (web.config) musi zostać zmodyfikowany dla aplikacji internetowych, przekierowania powiązań nie są automatycznie dodawane do pliku konfiguracji. Jednak program Visual Studio powiadamia o konfliktach powiązań, więc można dodać przekierowania powiązań, aby rozwiązać konflikty. Ponieważ zawsze monit o dodanie przekierowań powiązań, nie trzeba jawnie wyłączać tej funkcji dla aplikacji sieci web.

Aby dodać przekierowania powiązań do pliku web.config:

1. W programie Visual Studio skompiluj aplikację i sprawdź, czy występują ostrzeżenia kompilacji.

   ![Ostrzeżenie w przypadku konfliktów odwołanie do zestawu kompilacji](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Jeśli występują konflikty powiązań zestawów, zostanie wyświetlone ostrzeżenie. Kliknij dwukrotnie ostrzeżenie, lub Wybierz ostrzeżenie i naciśnij klawisz **Enter**.

   Zostanie wyświetlone okno dialogowe umożliwiające automatyczne dodanie niezbędnych przekierowań powiązań do źródłowego pliku web.config.

   ![Okno dialogowe uprawnienia przekierowania powiązania](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Zobacz także

- [\<bindingRedirect > Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Przekierowywanie wersji zestawu](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
