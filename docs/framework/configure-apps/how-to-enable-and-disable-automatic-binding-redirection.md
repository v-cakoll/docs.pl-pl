---
title: Włączanie lub wyłączanie wygenerowany automatycznie przekierowania powiązań
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b6c9c3508c53e8a68a3f7e1cb12b6b6c95600e7b
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380106"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań

Podczas kompilowania aplikacji w programie Visual Studio przeznaczonych dla platformy .NET Framework 4.5.1 i nowszych wersjach, przekierowania powiązań mogą automatycznie dodawane do pliku konfiguracji aplikacji w celu zastąpienia ujednolicenia zestawów. Przekierowania powiązań są dodawane, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu, nawet jeśli przekierowania powiązań zostaną określone ręcznie w pliku konfiguracji aplikacji. Funkcja automatycznego przekierowywania powiązań ma wpływ na aplikacje pulpitu i aplikacje sieci web przeznaczonych dla platformy .NET Framework 4.5.1 lub nowszej, chociaż zachowanie jest nieco inne w przypadku aplikacji sieci web. Można włączyć automatyczne przekierowywanie powiązań, jeśli masz istniejące aplikacje w tym docelowymi są poprzednie wersje programu .NET Framework lub wyłączyć tę funkcję, jeśli chcesz ręcznie tworzyć przekierowania powiązań.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Wyłączyć automatyczne przekierowywanie powiązań w aplikacjach klasycznych

Automatyczne przekierowania powiązań są domyślnie włączone dla aplikacji komputerowych Windows przeznaczonych dla środowiska .NET Framework 4.5.1 lub nowszy. Przekierowania powiązań są dodawane do konfiguracji danych wyjściowych (**app.config**) plik, gdy aplikacja jest kompilowana i zastąpienia ujednolicenia zestawów, które mogłoby mieć miejsce. Źródło **app.config** plik nie został zmodyfikowany. Tę funkcję można wyłączyć, modyfikując plik projektu dla aplikacji lub usunięcie zaznaczenia pola wyboru w oknie właściwości projektu w programie Visual Studio.

### <a name="disable-through-project-properties"></a>Wyłączyć za pomocą właściwości projektu

Jeśli masz program Visual Studio 2017 w wersji 15.7 lub nowszej, łatwo można wyłączyć przekierowania powiązań automatycznie wygenerowana na stronach właściwości projektu.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**.

2. Na **aplikacji** strony, usuń zaznaczenie pola wyboru **automatycznego generowania przekierowania powiązań** opcji.

3. Naciśnij klawisz **Ctrl**+**S** można zapisać zmiany.

### <a name="disable-manually-in-the-project-file"></a>Wyłącz ręcznie w pliku projektu

1. Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:

   - W programie Visual Studio wybierz projekt w **Eksploratora rozwiązań**, a następnie wybierz **Otwórz Folder w Eksploratorze plików** z menu skrótów. W Eksploratorze plików Znajdź plik projektu (.csproj lub .vbproj), a następnie otwórz go w Notatniku.
   - W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**. Ponownie kliknij prawym przyciskiem myszy zwolnionego projektu, a następnie wybierz **Edytuj [projectname.csproj]** .

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
   - W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**. Ponownie kliknij prawym przyciskiem myszy zwolnionego projektu, a następnie wybierz **Edytuj [projectname.csproj]** .

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

Automatyczne przekierowania powiązań są w przypadku aplikacji internetowych implementowane w inny sposób. Ponieważ konfiguracja źródła (**web.config**) plik musi zostać zmodyfikowany dla aplikacji sieci web, przekierowania powiązań nie są automatycznie dodawane do pliku konfiguracji. Jednak program Visual Studio powiadamia o konfliktach powiązań, więc można dodać przekierowania powiązań, aby rozwiązać konflikty. Ponieważ zawsze monit o dodanie przekierowań powiązań, nie trzeba jawnie wyłączać tej funkcji dla aplikacji sieci web.

Aby dodać przekierowania powiązań do **web.config** pliku:

1. W programie Visual Studio skompiluj aplikację i sprawdź, czy występują ostrzeżenia kompilacji.

   ![Ostrzeżenie w przypadku konfliktów odwołanie do zestawu kompilacji](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Jeśli występują konflikty powiązań zestawów, zostanie wyświetlone ostrzeżenie. Kliknij dwukrotnie ostrzeżenie, lub Wybierz ostrzeżenie i naciśnij klawisz **Enter**.

   Okno dialogowe, która umożliwia automatyczne dodawanie powiązania niezbędne przekierowuje do źródła **web.config** pojawia się w pliku.

   ![Okno dialogowe uprawnienia przekierowania powiązania](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Zobacz także

- [\<bindingRedirect> Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Przekierowywanie wersji zestawu](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
