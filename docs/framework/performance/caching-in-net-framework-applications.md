---
title: Buforowanie w aplikacjach .NET Framework
description: Używanie buforowania w aplikacjach .NET. Przeczytaj informacje o buforowaniu danych, buforowaniu w aplikacjach ASP.NET lub usługach REST WCF oraz rozszerzaniu buforowania w programie .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
ms.openlocfilehash: 9b08a07e9b446c2998150a327dccdc8d0481722a
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309771"
---
# <a name="caching-in-net-framework-applications"></a>Buforowanie w aplikacjach .NET Framework
Buforowanie umożliwia przechowywanie danych w pamięci w celu szybkiego dostępu. Po ponownym uzyskaniu dostępu do danych aplikacje mogą pobrać dane z pamięci podręcznej, zamiast pobierać je z oryginalnego źródła. Może to poprawić wydajność i skalowalność. Ponadto buforowanie sprawia, że dane są dostępne, gdy źródło danych jest tymczasowo niedostępne.  
  
 .NET Framework udostępnia funkcje buforowania, za pomocą których można poprawić wydajność i skalowalność aplikacji klienta i serwera systemu Windows, w tym ASP.NET.  
  
> [!NOTE]
> W .NET Framework 3,5 i starszych wersjach ASP.NET podał implementację pamięci podręcznej w pamięci w <xref:System.Web.Caching> przestrzeni nazw. W poprzednich wersjach .NET Framework buforowanie było dostępne tylko w <xref:System.Web> przestrzeni nazw i dlatego wymaga zależności od klas ASP.NET. W .NET Framework 4 <xref:System.Runtime.Caching> przestrzeń nazw zawiera interfejsy API przeznaczone dla aplikacji sieci Web i innych niż aplikacje sieci Web.  
  
## <a name="caching-data"></a>Buforowanie danych  
 Informacje można buforować za pomocą klas w <xref:System.Runtime.Caching> przestrzeni nazw. Klasy buforowania w tej przestrzeni nazw zapewniają następujące funkcje:  
  
- Typy abstrakcyjne, które stanowią podstawę do tworzenia niestandardowych implementacji pamięci podręcznej.  
  
- Konkretna implementacja pamięci podręcznej obiektów w pamięci.  
  
 Abstrakcyjna klasa podstawowej pamięci podręcznej ( <xref:System.Runtime.Caching.ObjectCache> ) definiuje następujące zadania buforowania:  
  
- Tworzenie i zarządzanie wpisami pamięci podręcznej.  
  
- Określanie informacji o wygasaniu i wykluczeniu.  
  
- Wyzwalanie zdarzeń, które są wywoływane w odpowiedzi na zmiany wpisów w pamięci podręcznej.  
  
 <xref:System.Runtime.Caching.MemoryCache>Klasa jest implementacją pamięci podręcznej obiektów w pamięci <xref:System.Runtime.Caching.ObjectCache> . W <xref:System.Runtime.Caching.MemoryCache> przypadku większości zadań buforowania można użyć klasy.  
  
> [!NOTE]
> <xref:System.Runtime.Caching.MemoryCache>Klasa jest modelowana na obiekcie pamięci podręcznej ASP.NET, który jest zdefiniowany w <xref:System.Web.Caching> przestrzeni nazw. W związku z tym wewnętrzna logika buforowania podobna do logiki podanej we wcześniejszych wersjach ASP.NET.  
  
 Aby zapoznać się z przykładem użycia do buforowania w aplikacji WPF, zobacz [Przewodnik: buforowanie danych aplikacji w aplikacji WPF](../wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>Buforowanie w aplikacjach ASP.NET  
 Klasy buforowania w <xref:System.Runtime.Caching> przestrzeni nazw zapewniają funkcjonalność buforowania danych w ASP.NET.  
  
> [!NOTE]
> Jeśli aplikacja jest przeznaczona dla .NET Framework 3,5 lub starszej, należy użyć klas buforowania, które są zdefiniowane w <xref:System.Web.Caching> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Omówienie buforowania ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
> [!NOTE]
> Podczas tworzenia nowych aplikacji zaleca się użycie <xref:System.Runtime.Caching.MemoryCache> klasy. Interfejs API, który znajduje się w <xref:System.Runtime.Caching> przestrzeni nazw, jest podobny do interfejsu API, który znajduje się w <xref:System.Web.Caching.Cache> przestrzeni nazw. W związku z tym interfejs API będzie znać użycie buforowania we wcześniejszych wersjach programu ASP.NET. Aby zapoznać się z przykładem użycia buforowania w aplikacjach ASP.NET, zobacz [Przewodnik: buforowanie danych aplikacji w ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100)).  
  
### <a name="output-caching"></a>Buforowanie danych wyjściowych  
 Aby ręcznie buforować dane aplikacji, można użyć <xref:System.Runtime.Caching.MemoryCache> klasy w ASP.NET. ASP.NET obsługuje również buforowanie danych wyjściowych, które przechowuje wygenerowane dane wyjściowe stron, kontrolek i odpowiedzi HTTP w pamięci. Buforowanie danych wyjściowych można skonfigurować deklaratywnie na stronie sieci Web ASP.NET lub za pomocą ustawień w pliku Web.config. Aby uzyskać więcej informacji, zobacz [OutputCache element for buforowanie (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228124(v=vs.100)).  
  
 ASP.NET umożliwia rozszerzoną buforowanie danych wyjściowych przez tworzenie niestandardowych dostawców pamięci podręcznej. Za pomocą dostawców niestandardowych można przechowywać zawartość pamięci podręcznej przy użyciu innych urządzeń magazynujących, takich jak dyski, magazyn w chmurze i rozproszone bufory pamięci podręcznej. Aby utworzyć niestandardowego dostawcę wyjściowej pamięci podręcznej, należy utworzyć klasę pochodzącą od <xref:System.Web.Caching.OutputCacheProvider> klasy i skonfigurować aplikację tak, aby korzystała z niestandardowego dostawcy wyjściowej pamięci podręcznej.  
  
## <a name="caching-in-wcf-rest-services"></a>Buforowanie w usługach REST WCF  
 W przypadku usług WCF REST .NET Framework umożliwia korzystanie z deklaracyjnego buforowania danych wyjściowych, które jest dostępne w ASP.NET. Dzięki temu można buforować odpowiedzi z operacji usługi REST platformy WCF. Gdy użytkownik wysyła żądanie HTTP GET do usługi, która jest skonfigurowana do buforowania, ASP.NET wysyła ponownie buforowaną odpowiedź, a metoda usługi nie jest wywoływana. Po wygaśnięciu pamięci podręcznej, gdy użytkownik wyśle żądanie HTTP GET, wywoływana jest metoda usługi i odpowiedź zostanie ponownie zbuforowana.  
  
 .NET Framework również umożliwia wdrożenie warunkowego buforowania HTTP GET. W przypadku scenariuszy REST warunkowe żądanie HTTP GET jest często używane przez usługi do implementowania inteligentnego buforowania HTTP zgodnie z opisem w [specyfikacji protokołu HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html). Aby uzyskać więcej informacji, zobacz [buforowanie obsługi usług HTTP sieci Web w programie WCF](../wcf/feature-details/caching-support-for-wcf-web-http-services.md).  
  
## <a name="extending-caching-in-the-net-framework"></a>Rozszerzanie buforowania w .NET Framework  
 Buforowanie w .NET Framework zostało zaprojektowane do rozszerzalności. <xref:System.Runtime.Caching.ObjectCache>Klasa pozwala utworzyć niestandardową implementację pamięci podręcznej. Ta klasa zawiera elementy członkowskie, które są dostępne dla wszystkich zarządzanych aplikacji, w tym Windows Forms, Windows Presentation Foundation (WPF) i Windows Communications Foundation (WCF). Można to zrobić, aby utworzyć klasę pamięci podręcznej, która korzysta z innego mechanizmu magazynu, lub jeśli chcesz uzyskać szczegółową kontrolę nad operacjami pamięci podręcznej.  
  
 Aby zwiększyć pamięć podręczną, można wykonać następujące czynności:  
  
- Utwórz klasę niestandardową, która dziedziczy z <xref:System.Runtime.Caching.ObjectCache> klasy, a następnie podaj implementację niestandardowej pamięci podręcznej w klasie pochodnej.  
  
- Utwórz klasę, która dziedziczy z <xref:System.Runtime.Caching.MemoryCache> klasy i dostosowuje lub zwiększa klasę pochodną. Aby zapoznać się z przykładem, zobacz [buforowanie danych aplikacji przy użyciu wielu obiektów pamięci podręcznej w aplikacji ASP.NET](https://docs.microsoft.com/archive/blogs/aspnetue/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application).  
  
- Utwórz klasę pochodzącą od <xref:System.Web.Caching.OutputCacheProvider> klasy i skonfiguruj aplikację tak, aby korzystała z niestandardowego dostawcy wyjściowej pamięci podręcznej.  
  
 Aby uzyskać więcej informacji, zobacz temat [buforowanie danych wyjściowych w systemie ASP.NET 4 (w programie VS 2010 i .net 4,0 Series)](https://weblogs.asp.net/scottgu/extensible-output-caching-with-asp-net-4-vs-2010-and-net-4-0-series) na blogu Scott Guthrie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF](../wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [Przewodnik: buforowanie danych aplikacji w ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))
