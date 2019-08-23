---
title: Włączanie lub wyłączanie przekierowań automatycznie generowanych powiązań
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: 178d5070dd7018bbc0fce474cdd0b31ba3d17f77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913034"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań

W przypadku kompilowania aplikacji w programie Visual Studio, które są przeznaczone dla .NET Framework 4.5.1 i nowszych wersji, przekierowania powiązań mogą być automatycznie dodawane do pliku konfiguracji aplikacji w celu zastąpienia zjednoczenia zestawu. Przekierowania powiązań są dodawane, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu, nawet jeśli przekierowania powiązań zostaną określone ręcznie w pliku konfiguracji aplikacji. Funkcja automatycznego przekierowywania powiązań ma wpływ na aplikacje pulpitu i aplikacje sieci Web, które są przeznaczone dla .NET Framework 4.5.1 lub nowszej wersji, chociaż zachowanie jest nieco inne dla aplikacji sieci Web. Automatyczne przekierowywanie powiązań można włączyć, jeśli istnieją aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework, lub wyłączyć tę funkcję, jeśli chcesz ręcznie tworzyć przekierowania powiązań.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Wyłączanie automatycznego przekierowywania powiązań w aplikacjach klasycznych

Automatyczne przekierowania powiązań są domyślnie włączone dla aplikacji klasycznych systemu Windows, które są przeznaczone dla .NET Framework 4.5.1 i nowszych wersji. Przekierowania powiązań są dodawane do pliku konfiguracji danych wyjściowych (**App. config**), gdy aplikacja jest kompilowana i przesłania nieujednolicenie zestawu, który może być w innym przypadku. Plik źródłowy **App. config** nie jest modyfikowany. Tę funkcję można wyłączyć, modyfikując plik projektu dla aplikacji lub zaznaczając zaznaczenie pola wyboru we właściwościach projektu w programie Visual Studio.

### <a name="disable-through-project-properties"></a>Wyłącz za poorednictwem właściwości projektu

Jeśli masz program Visual Studio 2017 w wersji 15,7 lub nowszej, możesz łatwo wyłączyć automatycznie generowane przekierowania powiązań na stronach właściwości projektu.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**.

2. Na stronie **aplikacja** Usuń zaznaczenie opcji **automatycznie Generuj powiązania powiązań** .

3. Naciśnij **kombinację klawiszy CTRL**+**S** , aby zapisać zmiany.

### <a name="disable-manually-in-the-project-file"></a>Wyłącz ręcznie w pliku projektu

1. Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:

   - W programie Visual Studio wybierz projekt w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików** z menu skrótów. W Eksploratorze plików Znajdź plik projektu (. csproj lub. vbproj) i otwórz go w Notatniku.
   - W programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**. Ponownie kliknij prawym przyciskiem myszy niezaładowanego projektu, a następnie wybierz polecenie **Edytuj [ProjectName. csproj]** .

2. W pliku projektu znajdź następujący wpis właściwości:

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Zmień `true` na `false`:

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Ręcznie Włącz automatyczne przekierowania powiązań

Automatyczne przekierowania powiązań można włączyć w istniejących aplikacjach przeznaczonych dla starszych wersji .NET Framework lub w przypadkach, gdy nie jest automatycznie wyświetlany monit o dodanie przekierowania. Jeśli celem jest nowsza wersja struktury, ale nie zostanie automatycznie wyświetlony monit o dodanie przekierowania, prawdopodobnie otrzymasz dane wyjściowe kompilacji, które sugerują ponowne mapowanie zestawów.

1. Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:

   - W programie Visual Studio wybierz projekt w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików** z menu skrótów. W Eksploratorze plików Znajdź plik projektu (. csproj lub. vbproj) i otwórz go w Notatniku.
   - W programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**. Ponownie kliknij prawym przyciskiem myszy niezaładowanego projektu, a następnie wybierz polecenie **Edytuj [ProjectName. csproj]** .

2. Dodaj następujący element do pierwszej grupy właściwości konfiguracji (w obszarze \<> tagu właściwości):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   Poniżej przedstawiono przykładowy plik projektu z wstawionym elementem:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. Skompiluj aplikację.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Włączanie automatycznego przekierowywania powiązań w aplikacjach sieci Web

Automatyczne przekierowania powiązań są w przypadku aplikacji internetowych implementowane w inny sposób. Ponieważ plik konfiguracji źródłowej (**Web. config**) musi zostać zmodyfikowany dla aplikacji sieci Web, przekierowania powiązań nie są automatycznie dodawane do pliku konfiguracji. Jednak program Visual Studio powiadamia o konfliktach powiązań, więc można dodać przekierowania powiązań, aby rozwiązać konflikty. Ponieważ zawsze jest wyświetlany monit o dodanie przekierowań powiązań, nie trzeba jawnie wyłączać tej funkcji dla aplikacji sieci Web.

Aby dodać przekierowania powiązań do pliku **Web. config** :

1. W programie Visual Studio skompiluj aplikację i sprawdź, czy występują ostrzeżenia kompilacji.

   ![Ostrzeżenie kompilacji dla konfliktów odwołań do zestawu](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Jeśli występują konflikty powiązań zestawów, zostanie wyświetlone ostrzeżenie. Kliknij dwukrotnie ostrzeżenie lub wybierz ostrzeżenie i naciśnij klawisz **Enter**.

   Zostanie wyświetlone okno dialogowe, które umożliwia automatyczne dodanie niezbędnych przekierowań powiązań do źródłowego pliku **Web. config** .

   ![Okno dialogowe uprawnień przekierowywania powiązań](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Zobacz także

- [\<bindingRedirect> Element](./file-schema/runtime/bindingredirect-element.md)
- [Przekierowywanie wersji zestawu](redirect-assembly-versions.md)
