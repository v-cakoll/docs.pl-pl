---
title: Buforowanie w aplikacjach .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
ms.openlocfilehash: a57489af2f2af59f128f5d86be844b43c9c49840
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085783"
---
# <a name="caching-in-net-framework-applications"></a>Buforowanie w aplikacjach .NET Framework
Pamięć podręczna umożliwia przechowywanie danych w pamięci, aby uzyskać szybki dostęp. Gdy dane są używane ponownie, aplikacje można uzyskać danych z pamięci podręcznej, zamiast pobierania z oryginalnego źródła. Może to poprawić wydajność i skalowalność. Ponadto buforowania sprawia, że dane dostępne, gdy źródłem danych jest tymczasowo niedostępna.  
  
 .NET Framework oferuje funkcje pamięci podręcznej, które można użyć w celu poprawy wydajności i skalowalności zarówno Windows klienta i serwera aplikacji, w tym ASP.NET.  
  
> [!NOTE]
>  W [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i wcześniejszych wersjach programu ASP.NET implementacji w pamięci podręcznej w <xref:System.Web.Caching> przestrzeni nazw. W poprzednich wersjach [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], pamięć podręczna była dostępna tylko w <xref:System.Web> przestrzeni nazw i dlatego wymagane zależności klas programu ASP.NET. W programie .NET Framework 4 <xref:System.Runtime.Caching> przestrzeń nazw zawiera interfejsy API, które są przeznaczone dla sieci Web, jak i innych aplikacji.  
  
## <a name="caching-data"></a>Buforowanie danych  
 Pamięci podręcznej informacje przy użyciu klas w <xref:System.Runtime.Caching> przestrzeni nazw. Buforowanie klasy w tej przestrzeni nazw zapewniają następujące funkcje:  
  
-   Typy abstrakcyjne, które stanowią podstawę do tworzenia implementacji niestandardowych pamięci podręcznej.  
  
-   Implementacja pamięci podręcznej konkretny obiekt w pamięci.  
  
 Abstrakcyjna Podstawowa pamięć podręczna klasy (<xref:System.Runtime.Caching.ObjectCache>) definiuje następujące zadania buforowania:  
  
-   Tworzenie i zarządzanie nimi wpisy w pamięci podręcznej.  
  
-   Określanie informacji dotyczących wygasania i eksmisji.  
  
-   Wyzwolenie zdarzenia, które są wywoływane w odpowiedzi na zmiany wpisy w pamięci podręcznej.  
  
 <xref:System.Runtime.Caching.MemoryCache> Klasa jest implementacją pamięci podręcznej obiektu w pamięci <xref:System.Runtime.Caching.ObjectCache> klasy. Możesz użyć <xref:System.Runtime.Caching.MemoryCache> klasy do wykonywania większości zadań buforowania.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> Klasy jest formowana obiektu pamięci podręcznej platformy ASP.NET, która jest zdefiniowana w <xref:System.Web.Caching> przestrzeni nazw. W związku z tym wewnętrznej pamięci podręcznej logikę podobną do logiki, która została podana we wcześniejszych wersjach programu ASP.NET.  
  
 Na przykład sposobu użycia do buforowania w aplikacji WPF, zobacz [instruktażu: Buforowanie danych aplikacji w aplikacji WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>Buforowanie w aplikacjach ASP.NET  
 Buforowanie klas w <xref:System.Runtime.Caching> przestrzeni nazw zapewnienia funkcji buforowania danych w programie ASP.NET.  
  
> [!NOTE]
>  Jeśli Twoje cele aplikacji [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] lub wcześniej, należy użyć buforowania klas, które są zdefiniowane w <xref:System.Web.Caching> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [program ASP.NET buforowanie Przegląd](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
> [!NOTE]
>  Podczas tworzenia nowych aplikacji zaleca się używanie <xref:System.Runtime.Caching.MemoryCache> klasy. Interfejs API, który znajduje się w <xref:System.Runtime.Caching> przestrzeni nazw jest jak interfejs API, który znajduje się w <xref:System.Web.Caching.Cache> przestrzeni nazw. W związku z tym interfejs API będą niczym nowym, jeśli użyto pamięci podręcznej we wcześniejszych wersjach programu ASP.NET. Na przykład jak używać buforowania w aplikacjach ASP.NET, zobacz [instruktażu: Buforowanie danych aplikacji na platformie ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100)).  
  
### <a name="output-caching"></a>Buforowanie danych wyjściowych  
 Aby ręcznie aplikacji danych z pamięci podręcznej, można użyć <xref:System.Runtime.Caching.MemoryCache> klasy w programie ASP.NET. ASP.NET obsługuje również buforowania danych wyjściowych, który przechowuje w pamięci wygenerowanych danych wyjściowych strony, kontrolek i odpowiedzi HTTP. Można skonfigurować w sposób deklaratywny buforowania danych wyjściowych na stronie sieci Web platformy ASP.NET lub przy użyciu ustawień w pliku Web.config. Aby uzyskać więcej informacji, zobacz [outputCache elemencie dla buforowania (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228124(v=vs.100)).  
  
 ASP.NET umożliwia rozszerzanie, buforowanie danych wyjściowych przez utworzenie niestandardowych dostawców pamięci podręcznej danych wyjściowych. Za pomocą dostawców niestandardowych, można przechowywać zawartość z pamięci podręcznej przy użyciu innych urządzeń magazynujących, takich jak dyski magazynu w chmurze i aparatów rozproszonej pamięci podręcznej. Aby utworzyć dostawcy pamięci podręcznej danych wyjściowych niestandardowych, należy utworzyć klasę, która pochodzi od klasy <xref:System.Web.Caching.OutputCacheProvider> klasy i konfigurowanie aplikacji do korzystania z danych wyjściowych niestandardowego dostawcy pamięci podręcznej.  
  
## <a name="caching-in-wcf-rest-services"></a>Buforowanie w usługach REST programu WCF  
 Dla usługi REST programu WCF programu .NET Framework umożliwia korzystanie z zalet buforowania danych wyjściowych deklaratywne, dostępnej w programie ASP.NET. To pozwala na buforowanie odpowiedzi z operacji usługi WCF REST. Po użytkownik wysyła żądanie HTTP GET do usługi, która jest skonfigurowana do buforowania, ASP.NET odsyła odpowiedzi z pamięci podręcznej i nie jest wywoływana metoda usługi. Po wygaśnięciu pamięci podręcznej, gdy następnym razem użytkownik wysyła żądanie HTTP GET jest wywoływana metoda usługi i odpowiedź jest zbuforowana z ponownie.  
  
 .NET Framework umożliwia także implementuje się buforowanie warunkowego HTTP GET. W pozostałych przypadkach warunkowego żądania HTTP GET jest często używana przez usługi do zaimplementowania buforowania inteligentnego HTTP, zgodnie z opisem w [specyfikację protokołu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800). Aby uzyskać więcej informacji, zobacz [buforowania pomocy technicznej dla usług HTTP sieci Web WCF](https://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>Rozszerzenie pamięci podręcznej w programie .NET Framework  
 Buforowanie w .NET Framework jest możliwość rozszerzenia. <xref:System.Runtime.Caching.ObjectCache> Klasy pozwala na tworzenie implementacji niestandardowych pamięci podręcznej. Ta klasa udostępnia elementy członkowskie, które są dostępne dla wszystkich aplikacji zarządzanych, w tym Windows Forms, Windows Presentation Foundation (WPF) i usług Windows Communications Foundation (WCF). Można to zrobić, aby można było utworzyć klasę pamięci podręcznej, która używa mechanizmu innego magazynu lub jeśli chcesz, aby precyzyjną kontrolę nad operacji pamięci podręcznej.  
  
 Rozszerzenie pamięci podręcznej można następujące możliwości:  
  
-   Utwórz klasę niestandardową, która pochodzi od klasy <xref:System.Runtime.Caching.ObjectCache> klasy, a następnie udostępnić implementację niestandardowej pamięci podręcznej w klasie pochodnej.  
  
-   Utwórz klasę, która pochodzi od klasy <xref:System.Runtime.Caching.MemoryCache> klasy i Dostosuj lub Rozszerz klasy pochodnej. Na przykład jak to zrobić, zobacz [buforowanie danych aplikacji przy użyciu wiele obiektów pamięci podręcznej w aplikacji ASP.NET](https://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
-   Utwórz klasę, która pochodzi od klasy <xref:System.Web.Caching.OutputCacheProvider> klasy i konfigurowanie aplikacji do korzystania z danych wyjściowych niestandardowego dostawcy pamięci podręcznej.  
  
 Aby uzyskać więcej informacji, zobacz wpis [Extensible buforowania danych wyjściowych platformy ASP.NET 4 (VS 2010 i .NET 4.0 seria)](https://go.microsoft.com/fwlink/?LinkId=185772) w blogu Scotta Guthrie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [Przewodnik: Buforowanie danych aplikacji na platformie ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))
