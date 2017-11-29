---
title: Buforowanie w aplikacjach .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
caps.latest.revision: "26"
author: tdykstra
ms.author: tdykstra
manager: wpickett
ms.openlocfilehash: 69e6ea6a95ffdea8f7a21540106d4817119a7cb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="caching-in-net-framework-applications"></a>Buforowanie w aplikacjach .NET Framework
Buforowanie umożliwia przechowywanie danych w pamięci, aby uzyskać szybki dostęp. Dostępie do danych ponownie, aplikacje można pobrać danych z pamięci podręcznej zamiast z oryginalnego źródła. Może to poprawić wydajność i skalowalność. Ponadto buforowanie sprawia, że nie są dostępne dane, gdy źródłem danych jest tymczasowo niedostępna.  
  
 .NET Framework udostępnia funkcję buforowania, używanego w celu poprawy wydajności i skalowalności zarówno systemu Windows na kliencie i serwerze aplikacji, w tym programu ASP.NET.  
  
> [!NOTE]
>  W [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i wcześniejszych wersjach programu ASP.NET dostępne implementację w pamięci podręcznej w <xref:System.Web.Caching> przestrzeni nazw. W poprzednich wersjach [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], buforowanie była dostępna tylko w <xref:System.Web> przestrzeni nazw i w związku z tym wymagana zależność klasy ASP.NET. W .NET Framework 4 <xref:System.Runtime.Caching> przestrzeń nazw zawiera interfejsy API, które są przeznaczone dla sieci Web i innych aplikacji.  
  
## <a name="caching-data"></a>Buforowanie danych  
 Pamięci podręcznej informacji przy użyciu klas w <xref:System.Runtime.Caching> przestrzeni nazw. Klasy buforowania w tej przestrzeni nazw zapewniają następujące funkcje:  
  
-   Typach abstrakcyjnych, które stanowią podstawę tworzenia implementacji niestandardowych pamięci podręcznej.  
  
-   Implementacja pamięci podręcznej konkretnego obiektu w pamięci.  
  
 Abstrakcyjna podstawowym buforowanie klasy (<xref:System.Runtime.Caching.ObjectCache>) definiuje następujące zadania buforowania:  
  
-   Tworzenie i zarządzanie nimi wpisy w pamięci podręcznej.  
  
-   Określanie informacji o wygaśnięciu i wykluczenia.  
  
-   Wyzwolenie zdarzenia, które zostały zgłoszone w odpowiedzi na zmiany w wpisy w pamięci podręcznej.  
  
 <xref:System.Runtime.Caching.MemoryCache> Klasa jest implementacją pamięci podręcznej w pamięci obiekt <xref:System.Runtime.Caching.ObjectCache> klasy. Można użyć <xref:System.Runtime.Caching.MemoryCache> klasy do wykonywania większości zadań buforowania.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> Klasy modelu dla obiektu pamięci podręcznej programu ASP.NET, który jest zdefiniowany w <xref:System.Web.Caching> przestrzeni nazw. W związku z tym wewnętrzna logiki buforowania podobne do logiki, które podano w starszych wersjach programu ASP.NET.  
  
 Na przykład sposobu użycia do buforowania w aplikacji WPF zobacz [wskazówki: buforowania danych aplikacji w aplikacji WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>Buforowanie w aplikacjach ASP.NET  
 Buforowanie klas w <xref:System.Runtime.Caching> przestrzeni nazw zapewniać funkcje do buforowania danych w programie ASP.NET.  
  
> [!NOTE]
>  Jeśli celów aplikacji [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] lub wcześniej, musisz użyć buforowania klas, które są zdefiniowane w <xref:System.Web.Caching> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [ASP.NET buforowanie omówienie](http://msdn.microsoft.com/library/5ec28012-4972-4dc3-b3e8-9d20401fe11d).  
  
> [!NOTE]
>  Podczas opracowywania nowych aplikacji, firma Microsoft zaleca użycie <xref:System.Runtime.Caching.MemoryCache> klasy. Interfejs API, który znajduje się w <xref:System.Runtime.Caching> przestrzeni nazw przypomina interfejs API, który znajduje się w <xref:System.Web.Caching.Cache> przestrzeni nazw. W związku z tym interfejsu API jest znane, jeśli używana jest buforowanie we wcześniejszych wersjach programu ASP.NET. Na przykład sposobu użycia buforowanie w aplikacjach ASP.NET, zobacz [wskazówki: buforowania danych aplikacji w programie ASP.NET](http://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23).  
  
### <a name="output-caching"></a>Buforowanie danych wyjściowych  
 Aby ręcznie aplikacji danych z pamięci podręcznej, można użyć <xref:System.Runtime.Caching.MemoryCache> klasy w programie ASP.NET. Program ASP.NET obsługuje również buforowanie danych wyjściowych, który przechowuje w pamięci wygenerowanych danych wyjściowych stron, kontrolek i odpowiedzi HTTP. Można skonfigurować deklaratywnie buforowanie danych wyjściowych na stronie sieci Web ASP.NET lub przy użyciu ustawień w pliku Web.config. Aby uzyskać więcej informacji, zobacz [outputCache Element do buforowania (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/en-us/47cd2b47-316f-4dfd-bbf8-539be3066fee).  
  
 Program ASP.NET pozwala rozszerzyć buforowania danych wyjściowych przez tworzenie niestandardowych dostawców pamięci podręcznej danych wyjściowych. Przy użyciu dostawców niestandardowych, można przechowywać zawartość z pamięci podręcznej przy użyciu innych urządzeń pamięci masowej, takich jak dyski magazynu w chmurze i aparatów rozproszonej pamięci podręcznej. Aby utworzyć dostawcy niestandardowego wyjściowej pamięci podręcznej, należy utworzyć klasę, która jest pochodną <xref:System.Web.Caching.OutputCacheProvider> klasy i skonfigurować aplikację do używania dostawcy niestandardowego wyjściowej pamięci podręcznej.  
  
## <a name="caching-in-wcf-rest-services"></a>Buforowanie w usługach REST usługi WCF  
 .NET Framework dla usługi REST usługi WCF umożliwia zalet buforowania danych wyjściowych deklaratywne dostępnej w programie ASP.NET. Dzięki temu możesz do pamięci podręcznej odpowiedzi z operacji usługi WCF REST. Gdy użytkownik wysyła żądanie HTTP GET do usługi, która jest skonfigurowana do buforowania, ASP.NET odsyła odpowiedź buforowana, a nie wywołano metody usługi. Po wygaśnięciu pamięci podręcznej, następnym razem, użytkownik wysyła żądanie HTTP GET jest wywoływana przez metodę usługi i ponownie buforowaną odpowiedź.  
  
 .NET Framework umożliwia także implementuje buforowanie warunkowego HTTP GET. W scenariuszach REST warunkowego żądanie HTTP GET jest często używane przez usługi do zaimplementowania inteligentne buforowanie HTTP zgodnie z opisem w [specyfikacji HTTP](http://go.microsoft.com/fwlink/?LinkId=165800). Aby uzyskać więcej informacji, zobacz [buforowanie obsługę usług HTTP sieci Web WCF](http://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>Rozszerzenie pamięci podręcznej w programie .NET Framework  
 Buforowanie w programie .NET Framework jest możliwość rozszerzenia. <xref:System.Runtime.Caching.ObjectCache> Klasa umożliwia tworzenie implementacji niestandardowych pamięci podręcznej. Ta klasa zawiera elementy członkowskie, które są dostępne dla wszystkich zarządzanych aplikacji, w tym formularzy systemu Windows, Windows Presentation Foundation (WPF) i Windows Communications Foundation (WCF). Można to zrobić, aby można było utworzyć klasę pamięci podręcznej, która korzysta z mechanizmu innego magazynu lub jeśli użytkownik chce szczegółową kontrolę nad operacji pamięci podręcznej.  
  
 Rozszerzenie pamięci podręcznej można można wykonaj następujące czynności:  
  
-   Tworzenie niestandardowej klasy, która jest pochodną <xref:System.Runtime.Caching.ObjectCache> klasy, a następnie udostępnić implementację niestandardowych pamięci podręcznej w klasie pochodnej.  
  
-   Utwórz klasę pochodną <xref:System.Runtime.Caching.MemoryCache> klasy i dostosować lub rozszerzyć klasy pochodnej. Na przykład jak to zrobić, zobacz [buforowanie danych aplikacji przy użyciu wielu obiektów pamięci podręcznej w aplikacji ASP.NET](http://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
-   Utwórz klasę pochodną <xref:System.Web.Caching.OutputCacheProvider> klasy i skonfigurować aplikację do używania dostawcy niestandardowego wyjściowej pamięci podręcznej.  
  
 Aby uzyskać więcej informacji, zobacz wpis [Extensible buforowanie danych wyjściowych z platformy ASP.NET 4 (VS 2010 i .NET 4.0 serii)](http://go.microsoft.com/fwlink/?LinkId=185772) na blogu Scott Guthrie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching.MemoryCache>  
 [Wskazówki: Buforowania danych aplikacji w aplikacji WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)  
 [Wskazówki: Buforowania danych aplikacji w programie ASP.NET](http://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23)
