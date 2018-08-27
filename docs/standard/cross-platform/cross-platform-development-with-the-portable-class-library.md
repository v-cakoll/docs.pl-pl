---
title: Tworzenie aplikacji dla wielu platform przy użyciu przenośnej biblioteki klas
ms.date: 07/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6c86870bf0089c25d402cf8f28a513e953ef28f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933706"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Tworzenie aplikacji dla wielu platform przy użyciu przenośnej biblioteki klas
Typ projektu przenośnej biblioteki klas .NET Framework w programie Visual Studio pomaga w tworzeniu aplikacji dla wielu platform i bibliotek dla platform firmy Microsoft, szybkie i łatwe.  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Biblioteki klas przenośnych mogą pomóc skrócić czas i koszt programowania oraz testowania kodu. Użyj tego typu projektu do zapisywania i tworzenia przenośnych zestawów .NET Framework, a następnie odwołuje się do tych zestawów z aplikacji przeznaczonych dla wielu platform, takich jak Windows i Windows Phone.  
  
 Nawet po Utwórz projekt biblioteki klas przenośnych w programie Visual Studio i zacznij programować go, możesz zmienić platformy docelowe. Program Visual Studio będzie kompilować biblioteki za pomocą nowych zestawów, który pomaga zidentyfikować zmiany, które należy wprowadzić w kodzie.  
  
 W tym artykule omówiono tworzenie aplikacji w programie Visual Studio, ale firma Microsoft udostępnia również Portable Class Library zestawy odwołań, które służą do tworzenia aplikacji i bibliotek z innych narzędzi, takich jak Xamarin. Te aplikacje i biblioteki można użyć w dowolnej runtime oparte na programie .NET Framework na platformach firmy Microsoft. Aby uzyskać więcej informacji na temat zestawów odwołań, zobacz wpis na blogu [przenośnych klasy biblioteki (PCL) teraz dostępne na wszystkich platformach](http://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx). Aby pobrać zestawy, zobacz [zestawy odwołań biblioteki przenośnej platformy .NET firmy Microsoft](http://www.microsoft.com/download/details.aspx?id=40727) w programie Microsoft Download Center. Aby uzyskać więcej informacji na temat używania zestawów za pomocą platformy Xamarin, zobacz wpis na blogu [PCL i bibliotek programu .NET NuGet teraz włączone dla programu Xamarin](http://blogs.msdn.com/b/dotnet/archive/2013/11/13/pcl-and-net-nuget-libraries-are-now-enabled-for-xamarin.aspx).  
  
 Visual Studio zawiera szablony ułatwiające opracowywanie z zastosowaniem biblioteki klas przenośnych. W zależności od tego, która wersja programu Visual Studio jest używany dostępne szablony i menu mogą się różnić od tych opisanych w tym artykule.  
  
> [!WARNING]
>  Visual Studio 2013 Update 2 obejmuje aktualizacje szablony Biblioteka klas przenośnych. Jeśli masz starszą wersję programu Visual Studio i Visual Studio 2013, zainstalowane na tym samym komputerze, a następnie zainstaluj Update 2, aby zmiany **platformę docelową** opcje zostaną zastosowane do obie wersje programu Visual Studio.  
  
 W tym temacie:  
  
 [Pomoc techniczna dla programu Visual Studio](#vs_support)  
 [Tworzenie projektu biblioteki klas przenośnych](#create_pcl)  
 [TARGET — opcje](#platforms)  
 [Zmiana obiektów docelowych](#change_targets)  
 [Obsługiwane funkcje](#features)  
 [Obsługiwane typy i elementy członkowskie](#members)  
 [Różnice interfejsu API w bibliotece klas przenośnych](#API_diff)  
 [Korzystanie z biblioteki klas przenośnych](#using)  
  
<a name="vs_support"></a>   
## <a name="visual-studio-support"></a>Pomoc techniczna dla programu Visual Studio  
 Visual Studio dla systemu Portable Class Library, zależy od wersji programu Visual Studio używasz. W niektórych przypadkach będziesz mieć wszystko, czego potrzebujesz, a w innych przypadkach należy zainstalować dodatkowe elementy, jak pokazano w poniższej tabeli.  
  
|Jednostka SKU programu Visual Studio|Pomoc techniczna dotycząca tworzenia biblioteki klas przenośnych|  
|-----------------------|---------------------------------------------------|  
|Program Visual Studio 2010, Professional, Premium lub Ultimate|Tak, po zainstalowaniu [narzędzia biblioteki przenośnej](https://marketplace.visualstudio.com/items?itemName=BCLTeam.PortableLibraryTools2).|  
|Wersje usługi Visual Studio Express 2010.|Nie.|  
|Visual Studio 2012 Professional, Premium lub Ultimate|Tak. W przypadku obsługi systemu Windows Phone 8.0, zainstalować [Windows Phone SDK 8.0](https://www.microsoft.com/download/details.aspx?id=35471).|  
|Wersje usługi Visual Studio Express 2012|Nie.|  
|Visual Studio 2013 Professional, Premium lub Ultimate|Tak. Obsługa systemu Windows Phone 8.1 można zainstalować [najnowszą wersję programu Visual Studio 2013](https://visualstudio.microsoft.com/vs/older-downloads/).|  
|Visual Studio Community 2013 for Windows|Tak, po zainstalowaniu [najnowszą wersję programu Visual Studio Community 2013](https://visualstudio.microsoft.com/vs/older-downloads/), która obejmuje Update 2.|  
  
<a name="create_pcl"></a>   
## <a name="creating-a-portable-class-library-project"></a>Tworzenie projektu biblioteki klas przenośnych  
 Aby utworzyć Portable Class Library, należy użyć jednego z szablonów w programie Visual Studio. Utwórz nowy projekt, a następnie w **nowy projekt** dialogowego **szablony**, wybierz swój język docelowy (C# lub Visual Basic), a następnie wybierz jedną z platform docelowych. Możesz wybrać dodatkowych platform, w następnym kroku.  
  
 W programie Visual Studio 2013 Update 2, można wybrać **Biblioteka klas (przenośna)** szablonu dla wybranego języka i platforma do tworzenia biblioteki klas przenośnych. Zostanie wyświetlony ten szablon dla następujących platform:  
  
-   Store Apps  
  
-   Windows Desktop  
  
-   Silverlight  
  
 Jeśli użytkownik chce utworzyć bibliotekę, aby obiekt docelowy systemu Windows Phone 8.1 i Windows 8.1 w języku C#, możesz wybrać **Store apps**, a następnie wybierz **biblioteki klas (przenośna dla aplikacji uniwersalnych)**.  
  
 ![Przenośnej biblioteki klas dla aplikacji Store](../../../docs/standard/cross-platform/media/storeuniversalpcl.png "StoreUniversalPCL")  
  
 Ten szablon automatycznie wybiera jako elementy docelowe Windows 8.1 i Windows Phone 8.1. Jeśli tworzysz bibliotekę, która dotyczy tylko systemu Windows Phone 8.1 lub Windows 8.1, możesz zmienić platformy docelowe i później dodać platform.  
  
 Jeśli używasz programu Visual Studio 2012 lub Visual Studio 2013 Update 2 — bez tworzenia nowego projektu i wybierz polecenie **Portable Class Library** szablonu w obszarze Visual C# lub Visual Basic.  
  
 ![Wybierz projekt przenośnej biblioteki](../../../docs/standard/cross-platform/media/portablelibrary-start.png "PortableLibrary_start")  
  
 **Dodaj Portable Class Library** pojawi się okno dialogowe i wybrać dodatkowych platform. Okno dialogowe zapewni ostrzeżenia dotyczącego zgodności na podstawie celów, którą wybierzesz.  
  
 ![Zmiana docelowej struktury okno dialogowe VS2013](../../../docs/standard/cross-platform/media/clr-pcl-changeframeworks.png "CLR_PCL_ChangeFrameworks")  
Dodaj okno dialogowe Portable Class Library dla programu Visual Studio 2013 Update 2  
  
 Niezależnie od tego, czy używasz programu Visual Studio 2012 lub Visual Studio 2013 możesz wybrać platformy, podczas tworzenia projektu Portable Class Library lub zmodyfikować platformy docelowe, po utworzeniu projektu można użyć właściwości projektu.  
  
<a name="platforms"></a>   
## <a name="target-options"></a>TARGET — opcje  
 Podczas tworzenia projektu Portable Class Library, możesz wybrać system operacyjny i wersja programu .NET Framework, który ma pod kątem. Jeśli używasz programu Visual Studio 2013 i po zainstalowaniu aktualizacji 2 lub nowszej, możesz wybrać **biblioteki klas (przenośna dla aplikacji uniwersalnych)** szablonu w celu utworzenia Portable Class Library, który jest przeznaczony dla Windows 8.1 i Windows Phone 8.1. W poniższej tabeli przedstawiono dostępne obiekty docelowe w zależności od wersji programu Visual Studio jest używany.  
  
|Opcja docelowej|Visual Studio 2012|Visual Studio 2013|Visual Studio 2013 Update 2 lub nowszy|  
|-|-|-|-|  
|.NET Framework|— Program .NET framework 4 lub nowszy<br /><br /> — Platforma .NET framework 4.0.3 lub nowszy<br /><br /> — Platforma .NET framework 4.5|— Program .NET framework 4 lub nowszy<br /><br /> — Platforma .NET framework 4.0.3 lub nowszy<br /><br /> — Program .NET framework 4.5 lub nowszy<br /><br /> — Platforma .NET framework 4.5.1|— Platforma .NET framework 4<br /><br /> — Platforma .NET framework 4.0.3<br /><br /> — Platforma .NET framework 4.5<br /><br /> — Platforma .NET framework 4.5.1|  
|Windows Phone|-Windows Phone 7 lub nowszy<br /><br /> -Windows Phone 7.5 i nowsze<br /><br /> -Windows Phone 8|-Windows Phone 8|-Windows Phone Silverlight 8<br /><br /> -Windows Phone Silverlight 8.1<br /><br /> Dla obsługi środowiska uruchomieniowego Windows i XAML należy wybrać:<br /><br /> -Windows Phone 8.1|  
|Sklep Windows|— Program .NET dla aplikacji Windows Store|-Windows Store Apps (system Windows 8) lub nowszy<br /><br /> -Windows Store Apps (Windows 8.1)|- Windows 8<br /><br /> - Windows 8.1|  
|-Program Silverlight|-Program Silverlight 4 i nowsze<br /><br /> -Program Silverlight 5|-Program Silverlight 5|-Program Silverlight 5|  
|Xbox|— Konsola Xbox 360|Brak|Brak|  
  
<a name="change_targets"></a>   
## <a name="changing-targets"></a>Zmiana obiektów docelowych  
 Wybierz szablon Portable Class Library, platformy domyślne są zaznaczone dla Ciebie, ale te wartości domyślne będą się różnić w zależności od instalowanej wersji programu Visual Studio został zainstalowany, a które elementy docelowe wybrano wcześniej. Można zmienić platformy, podczas tworzenia biblioteki klas przenośnych lub po rozpoczęciu tworzenia biblioteki klas przenośnych.  
  
 Jeśli chcesz zmienić elementy docelowe, po utworzeniu projektu w **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu biblioteki klas przenośnych (nie rozwiązanie), a następnie wybierz **właściwości** . Na stronie właściwości projektu **biblioteki** karta przedstawia platformy projektu obecnie dotyczy.  
  
 ![Właściwości projektu](../../../docs/standard/cross-platform/media/portablelibrary-projectproperties.png "PortableLibrary_ProjectProperties")  
Przenośne biblioteki klas strony właściwości dla programu Visual Studio 2013 Update 2  
  
 Aby dodać lub usunąć elementy docelowe, wybierz opcję **zmiany** przycisk, a następnie wybierz i usuń zaznaczenie pola wyboru.  
  
 Jeśli zmienisz docelowe, interfejsów API, które są dostępne i umożliwiają tworzenie projektu zmieni się na dopasować wybór. Visual Studio zgłasza błędy i ostrzeżenia, które może wyniknąć z elementów docelowych, zmiana.  
  
 Jeśli chcesz przeprowadzić ocenę przenośność zestawy przed wprowadzić zmiany w programie Visual Studio, można użyć [narzędzia .NET Portability Analyzer](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).  
  
 Opcje menu różnią się w zależności od wersji programu Visual Studio jest używany.  
  
 ![Zmień cel](../../../docs/standard/cross-platform/media/portablelibrary.png "PortableLibrary_")  
Okno dialogowe cele zmiany w programie Visual Studio 2012  
  
<a name="features"></a>   
## <a name="supported-features"></a>Obsługiwane funkcje  
 W poniższej tabeli przedstawiono funkcje obsługiwane na dostępnych platformach i wersjach. W niektórych przypadkach firma Microsoft dodała pomocy technicznej w wersji pakietu NuGet, a to zauważono. Aby uzyskać więcej informacji na temat pakietów NuGet dla programu .NET Framework, zobacz [.NET Framework i wersji Out-of-Band](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
|Funkcja|.NET Framework|.NET Framework|.NET Framework|Sklep Windows|Sklep Windows|Sklep Windows Phone|Windows Phone Silverlight|Windows Phone Silverlight|Windows Phone Silverlight|Silverlight|Silverlight|Xbox 360|  
|-------------|--------------------|--------------------|--------------------|-------------------|-------------------|-------------------------|-------------------------------|-------------------------------|-------------------------------|-----------------|-----------------|--------------|  
||**4**|**4.0.3**|**4.5**|**8**|**8.1**|**8.1**|**7.5**|**8**|**8.1**|**4**|**5**||  
|Podstawowe biblioteki|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
|Asynchroniczna pomoc techniczna|➊|➊|✓|✓|✓|✓|➊|➊|✓|➊|➊||  
|Kompresja|||✓|✓|✓|✓||➋|➋||||  
|Adnotacje danych||✓|✓|✓|✓|||||✓|✓||  
|Dynamiczne słowo kluczowe|✓|✓|✓|✓|✓|||||✓|✓||  
|Klasy HTTPClient|➌|➌|✓|✓|✓|✓|➌|➌|➌|➌|➌||  
|IQueryable|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Zapytanie o języku zintegrowanym (LINQ)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Sieci zarządzanych rozszerzeń (MEF)|✓|✓|✓|✓|✓|||||✓|✓||  
|Biblioteka klas sieciowych (NCL)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Serializacja (kontraktu danych XML i JSON)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|System.Numerics|✓|✓|✓|✓|✓|||||✓|✓||  
|Wyświetl modele (MVVM)|||✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Windows Communication Foundation (WCF)|✓|✓|✓|✓|✓||✓|✓|✓|✓|✓||  
|Interfejsów API środowiska wykonawczego Windows|||||✓|✓|||||||  
|Windows.UI.XAML|||||✓|✓|||||||  
|XLINQ||✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
  
 Wymaga ➊ [Microsoft Async](https://www.nuget.org/packages/Microsoft.Bcl.Async/) pakietu  
 Wymaga ➋ [Compression Microsoft](https://www.nuget.org/packages/Microsoft.Bcl.Compression) pakietu  
 Wymaga ➌ [biblioteki klienta HTTP Microsoft](https://www.nuget.org/packages/Microsoft.Net.Http) pakietu  
  
> [!WARNING]
>  Mogą wystąpić błędy, gdy odwołujesz się [Compression Microsoft](https://www.nuget.org/packages/Microsoft.Bcl.Compression) i [biblioteki klienta HTTP Microsoft](https://www.nuget.org/packages/Microsoft.Net.Http) pakietów z przenośnej biblioteki używane przez aplikację systemu Windows Phone Silverlight 8.1. Aby uzyskać więcej informacji, zobacz [zgodność z platformą i istotne zmiany w przypadku aplikacji systemu Windows Phone Silverlight 8.1](https://docs.microsoft.com/previous-versions/windows/apps/dn642084(v=vs.105)).  
  
<a name="members"></a>   
## <a name="supported-types-and-members"></a>Obsługiwane typy i elementy członkowskie  
 Typy i elementy członkowskie, które są dostępne w projektach Portable Class Library zależy od kilku czynników zgodności:  
  
-   Muszą one zostać udostępnione w lokalizacjach docelowych, które wybrano.  
  
-   Musi zachowywać się podobnie w tych lokalizacjach docelowych.  
  
-   Nie mogą być kandydatami do wycofania z użycia.  
  
-   Muszą mieć sens w środowisku przenośnym, zwłaszcza gdy pomocnicze elementy członkowskie nie są przenośne.  
  
 Na przykład biblioteki klas przenośnych zawiera typy związane z interfejsem użytkownika tylko wtedy, gdy miejscem docelowym Windows 8.1 i Windows Phone 8.1. Ponadto ograniczenia mogą wystąpić, jeśli platformą docelową jest platformy (np. Xbox, .NET Framework 4 i Windows Phone 7), które zostały wydane przed wprowadzeniem Portable Class Library. .NET Framework udostępnia pakiety za pośrednictwem pakietu NuGet, który zapewnia lepszą obsługę Portable Class Library, niektóre z tych starszych platformach. Aby uzyskać więcej informacji oraz listę pakietów NuGet, zobacz [.NET Framework i wersji Out-of-Band](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
 Jeśli członek jest obsługiwany, in Portable Class Library i wybrane elementy docelowe, pojawi się w projekcie w technologii IntelliSense. Ponadto, ikona Portable Class Library ![obsługiwane przez przenośnej biblioteki](../../../docs/standard/cross-platform/media/portablelibrary-referenceicon.png "PortableLibrary_ReferenceIcon") pojawia się w tabelach elementów członkowskich w [Biblioteka klas programu .NET Framework](https://msdn.microsoft.com/library/mt472912.aspx) obok obsługiwanych członków. Na przykład poniższa tabela elementów członkowskich pokazuje, że <xref:System.String.Chars%2A> właściwość <xref:System.String> klasy jest obsługiwana w Portable Class Library:  
  
 ![Obsługiwane ikonę elementu członkowskiego](../../../docs/standard/cross-platform/media/plibsupportedmemberlist.png "PlibSupportedMemberList")  
Ikona biblioteki klas przenośnych  
  
 Można również przeglądać **informacje o wersji** części tematu referencyjnego uwagą wskazującą, czy dany typ lub członek jest obsługiwany w projekcie biblioteki klas przenośnych:  
  
 ![Informacje o wersji biblioteki przenośnej](../../../docs/standard/cross-platform/media/plibversioninformation.png "PlibVersionInformation")  
Przykład — informacje o wersji  
  
 Należy jednak pamiętać, że interfejs API może być obsługiwana w Portable Class Library, ale czy można użyć interfejsu API zależy od celów wybierz.  
  
<a name="API_diff"></a>   
## <a name="api-differences-in-the-portable-class-library"></a>Różnice interfejsu API w bibliotece klas przenośnych  
 Aby zestawy Portable Class Library zgodne na wszystkich obsługiwanych platformach, niektórzy członkowie nieznacznie zmieniono in Portable Class Library.  
  
<a name="using"></a>   
## <a name="using-the-portable-class-library"></a>Używanie biblioteki klas przenośnych  
 Po skompilowaniu projektu Portable Class Library, możesz po prostu odwołanie do niego z innych projektów. Odwołanie może dotyczyć projektu lub określonych zestawów zawierających klasy, do których chce się uzyskać dostęp.  
  
 Aby uruchomić aplikację, która odwołuje się do zestawu Portable Class Library, wymagana wersja (lub nowszym) platformy docelowej musi być zainstalowany na tym komputerze. Program Visual Studio zawiera wszystkie wymagane struktury, aby można było uruchomić aplikację bez dalszych modyfikacji na komputerze, który jest używany do tworzenia aplikacji.  
  
### <a name="deploying-a-windows-store-or-windows-phone-app"></a>Wdrażanie aplikacji Windows Store lub Windows Phone  
 Podczas tworzenia Sklepu Windows lub aplikacji Windows Phone odwołujący się do zestawu Portable Class Library, wszystko, czego potrzebujesz do wdrażania aplikacji znajduje się w pakiecie aplikacji i nie trzeba wykonywać dalszych czynności są wymagane.  
  
### <a name="deploying-a-net-framework-app"></a>Wdrażanie .NET Framework aplikacji  
 Podczas wdrażania aplikacji .NET Framework, która odwołuje się do zestawu Portable Class Library, należy określić zależność od prawidłowej wersji programu .NET Framework. Określenie tej zależności gwarantuje, że wymagana wersja będzie instalowana wraz z aplikacją. Jeśli platformą docelową jest program .NET Framework 4 lub nowszy, komputer musi być .NET Framework 4 z [aktualizacji](https://www.microsoft.com/download/details.aspx?id=3556), aktualizacja 4.0.3 do programu .NET Framework 4 lub .NET Framework 4.5, zainstalowane.  
  
-   Aby utworzyć zależność z wdrożeniem ClickOnce: W **Eksploratora rozwiązań**, wybierz węzeł projektu dla projektu, który chcesz opublikować. (Jest to projekt, który odwołuje się do projektu Portable Class Library). Na pasku menu wybierz **projektu**, **właściwości**, a następnie wybierz **Publikuj** kartę. Na **Publikuj** wybierz **wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework (lub aktualizację programu .NET Framework 4).  
  
-   Aby utworzyć zależność z projektem Instalatora: W **Eksploratora rozwiązań**, wybierz projekt Instalatora. Na pasku menu wybierz **projektu**, **właściwości**, **wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.  
  
 Aby uzyskać więcej informacji na temat wdrażania aplikacji .NET Framework, zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
### <a name="deploying-a-silverlight-based-app"></a>Wdrażanie aplikacji opartych na technologii Silverlight  
 Podczas wdrażania aplikacji opartych na technologii Silverlight, który odwołuje się do zestawu Portable Class Library, upewnij się, że minimalna wymagana wersja wykonawcza dla aplikacji odpowiada wersją jej platformy docelowej. Jeśli platformą docelową jest program Silverlight 4, potrzebna jest wersja 4.0.60129.0 lub nowsza. Ustaw wersję umieszczając `<param name="minRuntimeVersion" value="4.0.60129.0" />` na stronie sieci Web, który jest hostem aplikacji opartych na technologii Silverlight w następujący sposób:  
  
```xaml  
<div id="silverlightControlHost">  
    <object data="data:application/x-silverlight-2,"   
           type="application/x-silverlight-2" width="100%" height="100%">  
    <param name="source" value="ClientBin/SilverlightApplication.xap"/>  
    <param name="onError" value="onSilverlightError" />  
    <param name="background" value="white" />  
    <param name="minRuntimeVersion" value="4.0.60129.0" />  
    <param name="autoUpgrade" value="true" />  
    <a href="https://www.microsoft.com/getsilverlight/get-started/install/"   
             style="text-decoration:none">  
      <img src=http://download.microsoft.com/download/5/1/6/5165823D-1D79-4871-8AC2-42DDDB94A5C2/PNGs/SLMedallion_ENU.png  
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
 [Narzędzia .NET portability Analyzer](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)  
 [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [Wdrażanie](../../../docs/framework/deployment/net-framework-applications.md)
