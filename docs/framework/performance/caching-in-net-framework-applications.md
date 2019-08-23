---
title: Buforowanie w aplikacjach .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
ms.openlocfilehash: 779785e9793939cf121fedf99b23a07288173637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967603"
---
# <a name="caching-in-net-framework-applications"></a>Buforowanie w aplikacjach .NET Framework
Buforowanie umożliwia przechowywanie danych w pamięci w celu szybkiego dostępu. Po ponownym uzyskaniu dostępu do danych aplikacje mogą pobrać dane z pamięci podręcznej, zamiast pobierać je z oryginalnego źródła. Może to poprawić wydajność i skalowalność. Ponadto buforowanie sprawia, że dane są dostępne, gdy źródło danych jest tymczasowo niedostępne.  
  
 .NET Framework udostępnia funkcje buforowania, za pomocą których można poprawić wydajność i skalowalność aplikacji klienta i serwera systemu Windows, w tym ASP.NET.  
  
> [!NOTE]
> W .NET Framework 3,5 i starszych wersjach ASP.NET podał implementację <xref:System.Web.Caching> pamięci podręcznej w pamięci w przestrzeni nazw. W poprzednich wersjach .NET Framework buforowanie było dostępne tylko w <xref:System.Web> przestrzeni nazw i dlatego wymaga zależności od klas ASP.NET. W .NET Framework 4 <xref:System.Runtime.Caching> przestrzeń nazw zawiera interfejsy API przeznaczone dla aplikacji sieci Web i innych niż aplikacje sieci Web.  
  
## <a name="caching-data"></a>Buforowanie danych  
 Informacje można buforować za pomocą klas w <xref:System.Runtime.Caching> przestrzeni nazw. Klasy buforowania w tej przestrzeni nazw zapewniają następujące funkcje:  
  
- Typy abstrakcyjne, które stanowią podstawę do tworzenia niestandardowych implementacji pamięci podręcznej.  
  
- Konkretna implementacja pamięci podręcznej obiektów w pamięci.  
  
 Abstrakcyjna klasa podstawowej pamięci podręcznej (<xref:System.Runtime.Caching.ObjectCache>) definiuje następujące zadania buforowania:  
  
- Tworzenie i zarządzanie wpisami pamięci podręcznej.  
  
- Określanie informacji o wygasaniu i wykluczeniu.  
  
- Wyzwalanie zdarzeń, które są wywoływane w odpowiedzi na zmiany wpisów w pamięci podręcznej.  
  
 Klasa jest implementacją <xref:System.Runtime.Caching.ObjectCache> pamięci podręcznej obiektów w pamięci. <xref:System.Runtime.Caching.MemoryCache> W przypadku większości zadań <xref:System.Runtime.Caching.MemoryCache> buforowania można użyć klasy.  
  
> [!NOTE]
> Klasa jest modelowana na obiekcie pamięci podręcznej ASP.NET, który jest zdefiniowany <xref:System.Web.Caching> w przestrzeni nazw. <xref:System.Runtime.Caching.MemoryCache> W związku z tym wewnętrzna logika buforowania podobna do logiki podanej we wcześniejszych wersjach ASP.NET.  
  
 Aby zapoznać się z przykładem użycia do buforowania w aplikacji WPF, zobacz [Przewodnik: Buforowanie danych aplikacji w aplikacji](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)WPF.  
  
## <a name="caching-in-aspnet-applications"></a>Buforowanie w aplikacjach ASP.NET  
 Klasy buforowania w <xref:System.Runtime.Caching> przestrzeni nazw zapewniają funkcjonalność buforowania danych w ASP.NET.  
  
> [!NOTE]
> Jeśli aplikacja jest przeznaczona dla .NET Framework 3,5 lub starszej, należy użyć klas buforowania, które są zdefiniowane w <xref:System.Web.Caching> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Omówienie buforowania ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
> [!NOTE]
> Podczas tworzenia nowych aplikacji zaleca się użycie <xref:System.Runtime.Caching.MemoryCache> klasy. Interfejs API, który znajduje się w <xref:System.Runtime.Caching> przestrzeni nazw, jest podobny do interfejsu API, który <xref:System.Web.Caching.Cache> znajduje się w przestrzeni nazw. W związku z tym interfejs API będzie znać użycie buforowania we wcześniejszych wersjach programu ASP.NET. Aby zapoznać się z przykładem użycia buforowania w aplikacjach ASP.NET, zobacz [Przewodnik: Buforowanie danych aplikacji w ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100)).  
  
### <a name="output-caching"></a>Buforowanie danych wyjściowych  
 Aby ręcznie buforować dane aplikacji, można użyć <xref:System.Runtime.Caching.MemoryCache> klasy w ASP.NET. ASP.NET obsługuje również buforowanie danych wyjściowych, które przechowuje wygenerowane dane wyjściowe stron, kontrolek i odpowiedzi HTTP w pamięci. Buforowanie danych wyjściowych można skonfigurować w sposób deklaratywny na stronie sieci Web ASP.NET lub za pomocą ustawień w pliku Web. config. Aby uzyskać więcej informacji, zobacz [OutputCache element for buforowanie (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228124(v=vs.100)).  
  
 ASP.NET umożliwia rozszerzoną buforowanie danych wyjściowych przez tworzenie niestandardowych dostawców pamięci podręcznej. Za pomocą dostawców niestandardowych można przechowywać zawartość pamięci podręcznej przy użyciu innych urządzeń magazynujących, takich jak dyski, magazyn w chmurze i rozproszone bufory pamięci podręcznej. Aby utworzyć niestandardowego dostawcę wyjściowej pamięci podręcznej, należy utworzyć klasę pochodzącą od <xref:System.Web.Caching.OutputCacheProvider> klasy i skonfigurować aplikację tak, aby korzystała z niestandardowego dostawcy wyjściowej pamięci podręcznej.  
  
## <a name="caching-in-wcf-rest-services"></a>Buforowanie w usługach REST WCF  
 W przypadku usług WCF REST .NET Framework umożliwia korzystanie z deklaracyjnego buforowania danych wyjściowych, które jest dostępne w ASP.NET. Dzięki temu można buforować odpowiedzi z operacji usługi REST platformy WCF. Gdy użytkownik wysyła żądanie HTTP GET do usługi, która jest skonfigurowana do buforowania, ASP.NET wysyła ponownie buforowaną odpowiedź, a metoda usługi nie jest wywoływana. Po wygaśnięciu pamięci podręcznej, gdy użytkownik wyśle żądanie HTTP GET, wywoływana jest metoda usługi i odpowiedź zostanie ponownie zbuforowana.  
  
 .NET Framework również umożliwia wdrożenie warunkowego buforowania HTTP GET. W przypadku scenariuszy REST warunkowe żądanie HTTP GET jest często używane przez usługi do implementowania inteligentnego buforowania HTTP zgodnie z opisem w [specyfikacji protokołu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800). Aby uzyskać więcej informacji, zobacz [buforowanie obsługi usług HTTP sieci Web w programie WCF](https://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>Rozszerzanie buforowania w .NET Framework  
 Buforowanie w .NET Framework zostało zaprojektowane do rozszerzalności. <xref:System.Runtime.Caching.ObjectCache> Klasa pozwala utworzyć niestandardową implementację pamięci podręcznej. Ta klasa zawiera elementy członkowskie, które są dostępne dla wszystkich zarządzanych aplikacji, w tym Windows Forms, Windows Presentation Foundation (WPF) i Windows Communications Foundation (WCF). Można to zrobić, aby utworzyć klasę pamięci podręcznej, która korzysta z innego mechanizmu magazynu, lub jeśli chcesz uzyskać szczegółową kontrolę nad operacjami pamięci podręcznej.  
  
 Aby zwiększyć pamięć podręczną, można wykonać następujące czynności:  
  
- Utwórz klasę niestandardową, która dziedziczy <xref:System.Runtime.Caching.ObjectCache> z klasy, a następnie podaj implementację niestandardowej pamięci podręcznej w klasie pochodnej.  
  
- Utwórz klasę, która dziedziczy z <xref:System.Runtime.Caching.MemoryCache> klasy i dostosowuje lub zwiększa klasę pochodną. Aby zapoznać się z przykładem, zobacz [buforowanie danych aplikacji przy użyciu wielu obiektów pamięci podręcznej w aplikacji ASP.NET](https://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
- Utwórz klasę pochodzącą od <xref:System.Web.Caching.OutputCacheProvider> klasy i skonfiguruj aplikację tak, aby korzystała z niestandardowego dostawcy wyjściowej pamięci podręcznej.  
  
 Aby uzyskać więcej informacji, zobacz temat [buforowanie danych wyjściowych w systemie ASP.NET 4 (w programie VS 2010 i .net 4,0 Series)](https://go.microsoft.com/fwlink/?LinkId=185772) na blogu Scott Guthrie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [Przewodnik: Buforowanie danych aplikacji w aplikacji WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [Przewodnik: Buforowanie danych aplikacji w ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))
