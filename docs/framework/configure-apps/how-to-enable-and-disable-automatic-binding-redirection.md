---
title: "Porady: włączanie i wyłączanie automatycznego przekierowania powiązań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 83b004934c303c95bdc4e6edb6031a86e2b1a6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Porady: włączanie i wyłączanie automatycznego przekierowania powiązań
Począwszy od [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], podczas kompilowania aplikacji przeznaczonych [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], przekierowania powiązań mogą być automatycznie dodawane do pliku konfiguracji aplikacji, aby zastąpić ujednolicenie zestawu. Przekierowania powiązań są dodawane, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu, nawet jeśli przekierowania powiązań zostaną określone ręcznie w pliku konfiguracji aplikacji. Funkcja przekierowania powiązania automatyczne wpływa na tradycyjnych aplikacji klasycznych i aplikacji sieci web przeznaczonych [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], chociaż to zachowanie różni się nieznacznie dla aplikacji sieci web. Można włączyć automatyczne przekierowywanie połączeń, jeśli są używane aplikacje, których platformami docelowymi są poprzednie wersje programu .NET Framework, ale można też wyłączyć tę funkcję, aby używać tworzonych ręcznie przekierowań powiązań.  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a>Wyłączanie automatycznego powiązanie przekierowuje w aplikacjach klasycznych  
 Przekierowania powiązania automatyczne są domyślnie włączone dla tradycyjnej aplikacji klasycznych, które odnoszą się do [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] i nowszych wersjach. Przekierowania powiązań są dodawane do wyjściowego pliku konfiguracji (app.config), gdy aplikacja jest kompilowana, co powoduje zastąpienie ujednolicenia zestawów, które mogłoby mieć miejsce. Źródłowy plik app.config nie jest modyfikowany. Tę funkcję można wyłączyć, modyfikując plik projektu dla aplikacji.  
  
#### <a name="to-disable-automatic-binding-redirects"></a>Aby wyłączyć automatyczne przekierowywanie powiązań  
  
1.  W programie Visual Studio, wybierz projekt **Eksploratora rozwiązań**, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików** z menu skrótów.  
  
2.  W Eksploratorze plików znajdź plik projektu (csproj lub vbproj) i otwórz go w Notatniku.  
  
3.  W pliku projektu znajdź następujący wpis właściwości:  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  Zmień `true` do `false`:  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a>Włączanie automatycznego powiązanie przekierowuje ręcznie  
 Można włączyć tego docelowego starsze wersje programu .NET Framework lub w przypadkach, gdy monit nie jest automatycznie dodać przekierowanie przekierowania powiązania automatyczne w istniejących aplikacji. Jeśli przeznaczona dla nowszej wersji platformy, ale nie będzie automatycznie monitowany dodać przekierowanie, prawdopodobnie otrzymasz dane wyjściowe kompilacji, które sugeruje się, że można ponownie zamapować zestawów.  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a>Aby ręcznie dodać właściwość przekierowania powiązania automatyczne  
  
1.  W programie Visual Studio, wybierz projekt **Eksploratora rozwiązań**, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików** z menu skrótów.  
  
2.  W Eksploratorze plików znajdź plik projektu (csproj lub vbproj) i otwórz go w Notatniku.  
  
3.  Dodaj następujący element do pierwszej grupy właściwości konfiguracji (w obszarze \<PropertyGroup > tagu):  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     Poniżej przedstawiono przykładowy plik projektu z wstawiony element.  
  
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
  
4.  Skompiluj aplikację.  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a>Włączanie automatycznego przekierowywania powiązań w aplikacjach sieci web  
 Automatyczne przekierowania powiązań są w przypadku aplikacji sieci web implementowane w inny sposób. Ponieważ źródłowy plik konfiguracji (web.config) musi zostać zmodyfikowany dla aplikacji sieci web, przekierowania powiązań nie są automatycznie dodawane do pliku konfiguracji. Jednak program Visual Studio powiadamia o konfliktach powiązań, więc można dodać przekierowania powiązań, aby rozwiązać konflikty. Zawsze jest wyświetlany monit o dodanie przekierowań powiązań, więc nie trzeba jawnie wyłączać tej funkcji dla aplikacji sieci web.  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a>Aby dodać przekierowania powiązań do pliku web.config  
  
1.  W programie Visual Studio skompiluj aplikację i sprawdź, czy występują ostrzeżenia kompilacji.  
  
     ![Ostrzeżenie dotyczące konflikty odwołań zestawu kompilacji](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")  
  
2.  Jeśli występują konflikty powiązań zestawów, zostanie wyświetlone ostrzeżenie. Kliknij dwukrotnie ostrzeżenie. (Klawiatury: Wybierz to ostrzeżenie i naciśnij klawisz **Enter**.)  
  
     Zostanie wyświetlone okno dialogowe umożliwiające automatyczne dodanie niezbędnych przekierowań powiązań do źródłowego pliku web.config.  
  
     ![Okno dialogowe uprawnienia przekierowania powiązania](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")  
  
## <a name="see-also"></a>Zobacz też  
 [\<w parametrze bindingRedirect > — Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [Przekierowywanie wersji zestawu](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
