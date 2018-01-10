---
title: "Tworzenie aplikacji dla wielu platform przy użyciu przenośnej biblioteki klas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
caps.latest.revision: "95"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea0a111727093cb65a98e48255b06b3c4516d258
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Tworzenie aplikacji dla wielu platform przy użyciu przenośnej biblioteki klas
Typ projektu biblioteki klas przenośnych .NET Framework w programie Visual Studio pomaga w utworzeniu wieloplatformowych aplikacji i bibliotek dla platform firmy Microsoft, szybkie i łatwe.  
  
 Biblioteki klas przenośnych mogą pomóc ograniczenia czasu i kosztów rozwijania i testowania kodu. Ten typ projektu służy do zapisu i utworzyć przenośne zestawy .NET Framework, a następnie odwołuje się do tych zestawów z aplikacji przeznaczonych dla wielu platform, takich jak system Windows i Windows Phone.  
  
 Nawet po utworzenia projektu biblioteki klas przenośnych w programie Visual Studio i rozpocząć tworzenie go, można zmienić na platformach docelowych. Visual Studio będzie kompilować biblioteki z nowego zestawów, który pomaga zidentyfikować zmiany, które należy wprowadzić w kodzie.  
  
 W tym artykule omówiono tworzenie aplikacji w programie Visual Studio, ale firma Microsoft udostępnia również zestawów odwołań przenośnej biblioteki klas, które służy do opracowywania aplikacji i bibliotek przy użyciu innych narzędzi, takich jak program Xamarin. Te aplikacje i bibliotek można użyć w dowolnej runtime opartych na programie .NET Framework na platformach firmy Microsoft. Aby uzyskać więcej informacji na temat zestawów odwołań, zobacz wpis na blogu [przenośne klasy biblioteki PCL () teraz dostępne na wszystkich platformach](http://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx). Aby pobrać zestawów, zobacz [Microsoft .NET przenośnej biblioteki odwołania zestawy](http://www.microsoft.com/download/details.aspx?id=40727) w programie Microsoft Download Center. Aby uzyskać więcej informacji o sposobie używania zestawy za pomocą platformy Xamarin, zobacz wpis na blogu [PCL i bibliotek NuGet .NET teraz włączone xamarin](http://blogs.msdn.com/b/dotnet/archive/2013/11/13/pcl-and-net-nuget-libraries-are-now-enabled-for-xamarin.aspx).  
  
 Program Visual Studio udostępnia szablony ułatwiające opracowanie z przenośnej biblioteki klas. W zależności od tego, czy używasz wersji programu Visual Studio dostępnych szablonów i menu może być inna niż opisane w tym artykule.  
  
> [!WARNING]
>  [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) obejmuje aktualizacje szablony przenośnej biblioteki klas. Jeśli masz starszą wersję programu Visual Studio i Visual Studio 2013 zainstalowany na tym samym komputerze, a następnie zainstaluj Update 2, aby zmiany **platformy docelowej** opcji zostaną zastosowane do obie wersje programu Visual Studio.  
  
 W tym temacie:  
  
 [Obsługa programu Visual Studio](#vs_support)  
 [Tworzenie projektu biblioteki klas przenośnych](#create_pcl)  
 [TARGET — opcje](#platforms)  
 [Zmiana obiektów docelowych](#change_targets)  
 [Obsługiwane funkcje](#features)  
 [Obsługiwane typy i elementy członkowskie](#members)  
 [Różnice interfejsu API w przenośnej biblioteki klas](#API_diff)  
 [Za pomocą biblioteki klas przenośnych](#using)  
  
<a name="vs_support"></a>   
## <a name="visual-studio-support"></a>Obsługa programu Visual Studio  
 Obsługa programu Visual Studio przenośnej biblioteki klas zależy od wersji programu Visual Studio używasz. W niektórych przypadkach będziesz mieć wszystko, czego potrzebujesz, a w pozostałych przypadkach musisz zainstalować dodatkowe elementy, jak pokazano w poniższej tabeli.  
  
|Visual Studio jednostki SKU|Obsługa tworzenia biblioteki klas przenośnych|  
|-----------------------|---------------------------------------------------|  
|Program Visual Studio 2010, Professional, Premium lub Ultimate|Tak, po zainstalowaniu [przenośne narzędzia biblioteki](https://marketplace.visualstudio.com/items?itemName=BCLTeam.PortableLibraryTools2).|  
|Wersje usługi Visual Studio Express 2010.|Nie.|  
|Program Visual Studio 2012 Professional, Premium lub Ultimate|Tak. Telefonów pomocy technicznej, należy zainstalować [Windows Phone SDK 8.0](http://go.microsoft.com/fwlink/?LinkId=265772).|  
|Visual Studio Express 2012 wersji|Nie.|  
|Program Visual Studio 2013 Professional, Premium lub Ultimate|Tak. Obsługa systemu Windows Phone 8.1, można zainstalować [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658).|  
|Visual Studio Express 2013 for Windows|Tak, po zainstalowaniu [najnowszej wersji programu Visual Studio Express](http://go.microsoft.com/fwlink/p/?LinkId=394629), która obejmuje Update 2 lub dodać [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658).|  
  
<a name="create_pcl"></a>   
## <a name="creating-a-portable-class-library-project"></a>Tworzenie projektu biblioteki klas przenośnych  
 Aby utworzyć przenośnej biblioteki klas, należy używać jednego z szablonów w programie Visual Studio. Utwórz nowy projekt i w **nowy projekt** okna dialogowego, w obszarze **szablony**, wybierz język docelowy (C# lub Visual Basic), a następnie wybierz jedną z platform docelową. Możesz wybrać dodatkowych platform w następnym kroku.  
  
 W programie Visual Studio 2013 Update 2, można wybrać **biblioteki klas (przenośna)** szablonu dla wybranego języka i platformy, aby utworzyć przenośnej biblioteki klas. Zostanie wyświetlony ten szablon dla następujących platform:  
  
-   Aplikacje ze sklepu  
  
-   System Windows Desktop  
  
-   Silverlight  
  
 Jeśli chcesz utworzyć bibliotekę docelowy Windows Phone 8.1 i Windows 8.1 w języku C#, możesz wybrać **aplikacji ze sklepu**, a następnie wybierz pozycję **biblioteki klas (przenośna dla aplikacji uniwersalnych)**.  
  
 ![Przenośna Biblioteka klas dla aplikacji ze sklepu](../../../docs/standard/cross-platform/media/storeuniversalpcl.png "StoreUniversalPCL")  
  
 Ten szablon automatycznie wybiera jako miejsca docelowe Windows 8.1 i Windows Phone 8.1. W przypadku utworzenia biblioteki, która dotyczy tylko systemu Windows Phone 8.1 lub Windows 8.1, można zmienić na platformach docelowych i później dodać platform.  
  
 Jeśli używasz programu Visual Studio 2012 lub Visual Studio 2013 Update 2 — bez tworzenia nowego projektu i wybierz polecenie **przenośnej biblioteki klas** szablonu w obszarze Visual C# lub Visual Basic.  
  
 ![Wybierz projektu biblioteki przenośnej](../../../docs/standard/cross-platform/media/portablelibrary-start.png "PortableLibrary_start")  
  
 **Dodać przenośnej biblioteki klas** zostanie wyświetlone okno dialogowe i wybrać dodatkowych platform. Okno dialogowe będzie przekazywać ostrzeżenia dotyczące zgodności, na podstawie celów, którą wybierzesz.  
  
 ![Zmiany docelowych platform w oknie dialogowym dla VS2013](../../../docs/standard/cross-platform/media/clr-pcl-changeframeworks.png "CLR_PCL_ChangeFrameworks")  
Dodaj — okno dialogowe przenośnej biblioteki klas dla programu Visual Studio 2013 Update 2  
  
 Niezależnie od tego, czy używasz programu Visual Studio 2012 lub Visual Studio 2013 możesz wybrać platformy, podczas tworzenia projektu przenośnej biblioteki klas lub właściwości projektu umożliwia modyfikowanie platformy docelowej po utworzeniu projektu.  
  
<a name="platforms"></a>   
## <a name="target-options"></a>TARGET — opcje  
 Podczas tworzenia projektu biblioteki klas przenośnych, można wybrać system operacyjny i wersja architektury .NET Framework, który ma być docelowa. Jeśli używasz programu Visual Studio 2013 i po zainstalowaniu aktualizacji 2 lub później, możesz wybrać **biblioteki klas (przenośna dla aplikacji uniwersalnych)** szablonu w celu utworzenia przenośnej biblioteki klas, przeznaczonego dla Windows 8.1 i Windows Phone 8.1. W poniższej tabeli przedstawiono dostępne elementy docelowe w zależności od wersji programu Visual Studio używasz.  
  
|Opcja docelowej|Visual Studio 2012|Visual Studio 2013|Visual Studio 2013 Update 2 lub nowszy|  
|-|-|-|-|  
|.NET Framework|-.NET framework 4 i nowsze<br /><br /> -.NET framework 4.0.3 i nowsze<br /><br /> -.NET framework 4.5|-.NET framework 4 i nowsze<br /><br /> -.NET framework 4.0.3 i nowsze<br /><br /> -.NET framework 4.5 lub nowszy<br /><br /> -.NET framework 4.5.1|-.NET framework 4<br /><br /> — Framework .NET 4.0.3<br /><br /> -.NET framework 4.5<br /><br /> -.NET framework 4.5.1|  
|Windows Phone|— Windows Phone 7 i nowsze<br /><br /> — Windows Phone 7.5 i nowsze<br /><br /> — Windows Phone 8|— Windows Phone 8|— Windows Phone Silverlight 8<br /><br /> — Windows Phone Silverlight 8.1<br /><br /> Obsługa środowiska uruchomieniowego systemu Windows i języka XAML wybierz:<br /><br /> — Windows Phone 8.1|  
|Sklep Windows|-.NET dla aplikacji ze Sklepu Windows|-Aplikacje ze Sklepu Windows (z systemem Windows 8) lub nowszy<br /><br /> — Aplikacje ze Sklepu Windows (Windows 8.1)|— Windows 8<br /><br /> — Windows 8.1|  
|-Silverlight|-Program Silverlight 4 i nowsze<br /><br /> -Silverlight 5|-Silverlight 5|-Silverlight 5|  
|Xbox|-Konsoli Xbox 360|Brak|Brak|  
  
<a name="change_targets"></a>   
## <a name="changing-targets"></a>Zmiana obiektów docelowych  
 Wybieranie szablonu przenośnej biblioteki klas, domyślna platformy wybrane są dla Ciebie, ale te wartości domyślne będą się różnić w zależności od wersji programu Visual Studio został zainstalowany, a które obiekty docelowe wybrano wcześniej. Platformy można zmienić po utworzeniu przenośnej biblioteki klas, lub po rozpoczęciu tworzenia przenośnej biblioteki klas.  
  
 Jeśli chcesz zmienić elementy docelowe, po utworzeniu projektu, w **Eksploratora rozwiązań**, otwórz menu skrótów projektu biblioteki klas przenośnych (nie rozwiązanie), a następnie wybierz **właściwości** . Na stronie właściwości projektu **biblioteki** kartę przedstawia platformy, że obecnie elementem docelowym projektu.  
  
 ![Właściwości projektu](../../../docs/standard/cross-platform/media/portablelibrary-projectproperties.png "PortableLibrary_ProjectProperties")  
Przenośnej biblioteki klas strony właściwości dla programu Visual Studio 2013 Update 2  
  
 Aby dodać lub usunąć elementy docelowe, wybierz **zmiany** przycisk, a następnie wybierz i usuń zaznaczenie pola wyboru.  
  
 Jeśli zmienisz elementy docelowe, interfejsów API, które są dostępne i umożliwiają tworzenie projektu zmieni się na dopasować wybór. Visual Studio zgłasza błędów i ostrzeżeń, które mogą wystąpić w wyniku elementy docelowe, zmiana.  
  
 Jeśli chcesz ocenić przenośność z zestawów przed wprowadzić zmiany w programie Visual Studio, możesz użyć [analizator przenośność .NET](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).  
  
 Opcje menu będą się różnić w zależności od wersji programu Visual Studio używasz.  
  
 ![Zmień docelowy](../../../docs/standard/cross-platform/media/portablelibrary.png "PortableLibrary_")  
Okno dialogowe zmiany elementów docelowych w programie Visual Studio 2012  
  
<a name="features"></a>   
## <a name="supported-features"></a>Obsługiwane funkcje  
 W poniższej tabeli przedstawiono funkcje obsługiwane na dostępnych platformach i wersjach. W niektórych przypadkach firma Microsoft dodała pomocy technicznej wraz z wydaniem pakietu NuGet, a to jest odnotowany. Aby uzyskać więcej informacji na temat pakietów NuGet dla programu .NET Framework, zobacz [.NET Framework i poza harmonogramem](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
|Funkcja|.NET Framework|.NET Framework|.NET Framework|Sklep Windows|Sklep Windows|Sklep Windows Phone|Windows Phone Silverlight|Windows Phone Silverlight|Windows Phone Silverlight|Silverlight|Silverlight|Xbox 360|  
|-------------|--------------------|--------------------|--------------------|-------------------|-------------------|-------------------------|-------------------------------|-------------------------------|-------------------------------|-----------------|-----------------|--------------|  
||**4**|**4.0.3**|**4.5**|**8**|**8.1**|**8.1**|**7.5**|**8**|**8.1**|**4**|**5**||  
|Podstawowe biblioteki|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
|Obsługa Async|➊|➊|✓|✓|✓|✓|➊|➊|✓|➊|➊||  
|Kompresja|||✓|✓|✓|✓||➋|➋||||  
|Adnotacje danych||✓|✓|✓|✓|||||✓|✓||  
|Dynamiczne słowo kluczowe|✓|✓|✓|✓|✓|||||✓|✓||  
|HTTPClient|➌|➌|✓|✓|✓|✓|➌|➌|➌|➌|➌||  
|IQueryable|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Zapytanie o języku zintegrowanym (LINQ)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Rozszerzalność zarządzanej sieci (MEF)|✓|✓|✓|✓|✓|||||✓|✓||  
|Biblioteka klas sieciowych (NCL)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Serializacja (kontraktu danych XML i JSON)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|System.Numerics|✓|✓|✓|✓|✓|||||✓|✓||  
|Wyświetlanie modeli (MVVM)|||✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Windows Communication Foundation (WCF)|✓|✓|✓|✓|✓||✓|✓|✓|✓|✓||  
|Interfejsy API środowiska wykonawczego systemu Windows|||||✓|✓|||||||  
|Windows.UI.XAML|||||✓|✓|||||||  
|XLINQ||✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
  
 Wymaga ➊ [Microsoft Async](https://www.nuget.org/packages/Microsoft.Bcl.Async/) pakietu  
 Wymaga ➋ [Compression Microsoft](https://www.nuget.org/packages/Microsoft.Bcl.Compression) pakietu  
 Wymaga ➌ [bibliotek klienta HTTP Microsoft](http://www.nuget.org/packages/Microsoft.Net.Http) pakietu  
  
> [!WARNING]
>  Mogą wystąpić błędy podczas tworzenia odwołania [Compression Microsoft](https://www.nuget.org/packages/Microsoft.Bcl.Compression) i [bibliotek klienta HTTP Microsoft](http://www.nuget.org/packages/Microsoft.Net.Http) pakietów z przenośnej biblioteki używany przez aplikację systemu Windows Phone Silverlight 8.1. Aby uzyskać więcej informacji, zobacz [zgodności platformy i fundamentalne zmiany dla aplikacji Windows Phone Silverlight 8.1](http://go.microsoft.com/fwlink/p/?LinkId=394744).  
  
<a name="members"></a>   
## <a name="supported-types-and-members"></a>Obsługiwane typy i elementy członkowskie  
 Typy i składniki, które są dostępne w projektach biblioteki klas przenośnych są ograniczone przez kilka czynników zgodności:  
  
-   Muszą one zostać udostępnione przez wybrane elementy docelowe.  
  
-   Należy zachowują się podobnie między tymi elementami docelowymi.  
  
-   Nie mogą być kandydatami do wycofania z użycia.  
  
-   Muszą mieć sens w środowisku przenośnym, zwłaszcza gdy pomocnicze elementy członkowskie nie są przenośne.  
  
 Na przykład przenośnej biblioteki klas zawiera typy związane z interfejsu użytkownika tylko wtedy, gdy zostanie rozpoczęta dla Windows 8.1 i Windows Phone 8.1. Ponadto można napotkać ograniczenia w przypadku skierowania platformy (na przykład konsoli Xbox, .NET Framework 4 i Windows Phone 7), które zostały wydane przed wprowadzeniem przenośnej biblioteki klas. .NET Framework zwalnia pakiety za pośrednictwem pakietu NuGet, który zapewnia lepszą obsługę przenośnej biblioteki klas, niektóre z tych starszych platformach. Aby uzyskać więcej informacji oraz listę pakietów NuGet, zobacz [.NET Framework i poza harmonogramem](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
 Jeśli element członkowski jest obsługiwany w przenośnej biblioteki klas i wybrane elementy docelowe, pojawi się w projekcie IntelliSense. Ponadto, ikona przenośnej biblioteki klas ![obsługiwane przez przenośnej biblioteki](../../../docs/standard/cross-platform/media/portablelibrary-referenceicon.png "PortableLibrary_ReferenceIcon") pojawia się w tabelach elementów członkowskich w [Biblioteka klas programu .NET Framework](https://msdn.microsoft.com/library/mt472912.aspx) dalej, aby obsługiwane elementy członkowskie. Na przykład w poniższej tabeli elementów członkowskich wskazuje, że <xref:System.String.Chars%2A> właściwości w <xref:System.String> klasa jest obsługiwana w przenośnej biblioteki klas:  
  
 ![Ikona składnika obsługiwanych](../../../docs/standard/cross-platform/media/plibsupportedmemberlist.png "PlibSupportedMemberList")  
Ikona biblioteki klas przenośnych  
  
 Można również sprawdzić **informacje o wersji** tematu odwołania, uwagi, wskazujący, że typ lub element członkowski jest obsługiwany w projekcie przenośnej biblioteki klas:  
  
 ![Informacje o wersji przenośnej biblioteki](../../../docs/standard/cross-platform/media/plibversioninformation.png "PlibVersionInformation")  
Przykład — informacje o wersji  
  
 Należy jednak pamiętać, interfejs API może być obsługiwana w przenośnej biblioteki klas, że czy można użyć interfejsu API jest zależna od obiektów docelowych można wybrać.  
  
<a name="API_diff"></a>   
## <a name="api-differences-in-the-portable-class-library"></a>Różnice interfejsu API w przenośnej biblioteki klas  
 Aby zapewnić zgodność zestawy przenośnej biblioteki klas na wszystkich obsługiwanych platformach, niektóre elementy członkowskie nieco zmieniono w przenośnej biblioteki klas.  
  
<a name="using"></a>   
## <a name="using-the-portable-class-library"></a>Używanie biblioteki klas przenośnych  
 Po utworzeniu projektu biblioteki klas przenośnych można po prostu się odwoływać z innych projektów. Odwołanie może dotyczyć projektu lub określonych zestawów zawierających klasy, do których chce się uzyskać dostęp.  
  
 Aby uruchomić aplikację, która odwołuje się do zestawu przenośnej biblioteki klas, wymaganej wersji (lub nowsza) platform docelowych musi być zainstalowany na tym komputerze. Visual Studio zawiera wszystkie wymagane struktury, więc można uruchomić aplikacji bez dalszej modyfikacji na komputerze, który został użyty do tworzenia aplikacji.  
  
### <a name="deploying-a-windows-store-or-windows-phone-app"></a>Wdrażanie aplikacji ze Sklepu Windows lub Windows Phone  
 Podczas tworzenia Sklepu Windows lub aplikacji Windows Phone odwołuje się zestaw przenośnej biblioteki klas, wszystkie elementy potrzebne do wdrożenia aplikacji jest uwzględniona w pakiet aplikacji i nie są wymagane żadne dodatkowe czynności.  
  
### <a name="deploying-a-net-framework-app"></a>Wdrażanie .NET Framework aplikacji  
 Podczas wdrażania aplikacji .NET Framework, która odwołuje się do zestawu przenośnej biblioteki klas, należy określić zależności na poprawną wersję programu .NET Framework. Określenie tej zależności gwarantuje, że wymagana wersja będzie instalowana wraz z aplikacją. Jeśli są przeznaczone dla platformy .NET Framework 4 lub nowszy, komputer musi mieć programu .NET Framework 4 z [aktualizacji](http://go.microsoft.com/fwlink/?LinkId=210824), aktualizacja 4.0.3 dla programu .NET Framework 4 lub .NET Framework 4.5 zainstalowane.  
  
-   Aby utworzyć zależność z wdrażania ClickOnce: W **Eksploratora rozwiązań**, wybierz węzeł projektu dla projektu, którą chcesz opublikować. (Jest to projekt, który odwołuje się do projektu biblioteki klas przenośnych). Na pasku menu wybierz **projektu**, **właściwości**, a następnie wybierz pozycję **publikowania** kartę. Na **publikowania** wybierz pozycję **wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework (lub aktualizację programu .NET Framework 4).  
  
-   Aby utworzyć zależność z projektu Instalatora: W **Eksploratora rozwiązań**, wybierz projekt Instalatora. Na pasku menu wybierz **projektu**, **właściwości**, **wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.  
  
 Aby uzyskać więcej informacji na temat wdrażania aplikacji .NET Framework, zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
### <a name="deploying-a-silverlight-based-app"></a>Wdrażanie aplikacji Silverlight  
 Podczas wdrażania aplikacji oparte na technologii Silverlight, który odwołuje się do zestawu przenośnej biblioteki klas musi upewnij się, że wersja wykonawcza minimalne wymagane dla aplikacji odpowiada jego wersję docelową. Jeśli platformą docelową jest program Silverlight 4, potrzebna jest wersja 4.0.60129.0 lub nowsza. Ustaw wersję umieszczając `<param name="minRuntimeVersion" value="4.0.60129.0" />` na stronie sieci Web, który jest hostem aplikacji oparte na technologii Silverlight w następujący sposób:  
  
```xaml  
<div id="silverlightControlHost">  
    <object data="data:application/x-silverlight-2,"   
           type="application/x-silverlight-2" width="100%" height="100%">  
    <param name="source" value="ClientBin/SilverlightApplication.xap"/>  
    <param name="onError" value="onSilverlightError" />  
    <param name="background" value="white" />  
    <param name="minRuntimeVersion" value="4.0.60129.0" />  
    <param name="autoUpgrade" value="true" />  
    <a href="http://go.microsoft.com/fwlink/?LinkID=149156&v=4.0.50826.0"   
             style="text-decoration:none">  
      <img src=http://go.microsoft.com/fwlink/?LinkId=161376  
             alt="Get Microsoft Silverlight" style="border-style:none"/>  
    </a>  
  </object>  
   <iframe id="_sl_historyFrame"   
              style="visibility:hidden;height:0px;width:0px;border:0px">  
   </iframe>  
</div>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z biblioteki klas przenośnych z modelem MVVM](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)  
 [Zasoby aplikacji dla bibliotek przeznaczonych do wielu platform](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)  
 [Analizator przenośność .NET](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)  
 [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [Wdrażanie](../../../docs/framework/deployment/net-framework-applications.md)
