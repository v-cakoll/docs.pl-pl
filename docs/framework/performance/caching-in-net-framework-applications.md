---
title: Buforowanie w aplikacjach .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
ms.openlocfilehash: 8fe2a386da8cdb4bb075b67a5e52c840a7b66c77
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935285"
---
# <a name="caching-in-net-framework-applications"></a>Buforowanie w aplikacjach .NET Framework
Buforowanie umożliwia przechowywanie danych w pamięci w celu szybkiego dostępu. Po ponownym uzyskaniu dostępu do danych aplikacje mogą pobrać dane z pamięci podręcznej, zamiast pobierać je z oryginalnego źródła. Może to poprawić wydajność i skalowalność. Ponadto buforowanie sprawia, że dane są dostępne, gdy źródło danych jest tymczasowo niedostępne.  
  
 .NET Framework udostępnia funkcje buforowania, za pomocą których można poprawić wydajność i skalowalność aplikacji klienta i serwera systemu Windows, w tym ASP.NET.  
  
> [!NOTE]
> W .NET Framework 3,5 i starszych wersjach ASP.NET podał implementację pamięci podręcznej w pamięci <xref:System.Web.Caching>. W poprzednich wersjach .NET Framework buforowanie było dostępne tylko w przestrzeni nazw <xref:System.Web> i dlatego wymaga zależności od klas ASP.NET. W .NET Framework 4 <xref:System.Runtime.Caching> przestrzeń nazw zawiera interfejsy API, które są przeznaczone dla aplikacji sieci Web i innych niż sieci Web.  
  
## <a name="caching-data"></a>Buforowanie danych  
 Informacje można buforować przy użyciu klas w przestrzeni nazw <xref:System.Runtime.Caching>. Klasy buforowania w tej przestrzeni nazw zapewniają następujące funkcje:  
  
- Typy abstrakcyjne, które stanowią podstawę do tworzenia niestandardowych implementacji pamięci podręcznej.  
  
- Konkretna implementacja pamięci podręcznej obiektów w pamięci.  
  
 Abstrakcyjna klasa podstawowej pamięci podręcznej (<xref:System.Runtime.Caching.ObjectCache>) definiuje następujące zadania buforowania:  
  
- Tworzenie i zarządzanie wpisami pamięci podręcznej.  
  
- Określanie informacji o wygasaniu i wykluczeniu.  
  
- Wyzwalanie zdarzeń, które są wywoływane w odpowiedzi na zmiany wpisów w pamięci podręcznej.  
  
 Klasa <xref:System.Runtime.Caching.MemoryCache> jest implementacją pamięci podręcznej obiektów klasy <xref:System.Runtime.Caching.ObjectCache>. W przypadku większości zadań buforowania można użyć klasy <xref:System.Runtime.Caching.MemoryCache>.  
  
> [!NOTE]
> Klasa <xref:System.Runtime.Caching.MemoryCache> jest modelowana na obiekcie pamięci podręcznej ASP.NET, który jest zdefiniowany w przestrzeni nazw <xref:System.Web.Caching>. W związku z tym wewnętrzna logika buforowania podobna do logiki podanej we wcześniejszych wersjach ASP.NET.  
  
 Aby zapoznać się z przykładem użycia do buforowania w aplikacji WPF, zobacz [Przewodnik: buforowanie danych aplikacji w aplikacji WPF](../wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>Buforowanie w aplikacjach ASP.NET  
 Klasy buforowania w przestrzeni nazw <xref:System.Runtime.Caching> zapewniają funkcję buforowania danych w ASP.NET.  
  
> [!NOTE]
> Jeśli aplikacja jest przeznaczona dla .NET Framework 3,5 lub starszej, należy użyć klas buforowania, które są zdefiniowane w przestrzeni nazw <xref:System.Web.Caching>. Aby uzyskać więcej informacji, zobacz [Omówienie buforowania ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
> [!NOTE]
> Podczas tworzenia nowych aplikacji zaleca się użycie klasy <xref:System.Runtime.Caching.MemoryCache>. Interfejs API, który jest dostępny w przestrzeni nazw <xref:System.Runtime.Caching>, jest podobny do interfejsu API, który znajduje się w przestrzeni nazw <xref:System.Web.Caching.Cache>. W związku z tym interfejs API będzie znać użycie buforowania we wcześniejszych wersjach programu ASP.NET. Aby zapoznać się z przykładem użycia buforowania w aplikacjach ASP.NET, zobacz [Przewodnik: buforowanie danych aplikacji w ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100)).  
  
### <a name="output-caching"></a>Buforowanie danych wyjściowych  
 Aby ręcznie buforować dane aplikacji, można użyć klasy <xref:System.Runtime.Caching.MemoryCache> w ASP.NET. ASP.NET obsługuje również buforowanie danych wyjściowych, które przechowuje wygenerowane dane wyjściowe stron, kontrolek i odpowiedzi HTTP w pamięci. Buforowanie danych wyjściowych można skonfigurować w sposób deklaratywny na stronie sieci Web ASP.NET lub za pomocą ustawień w pliku Web. config. Aby uzyskać więcej informacji, zobacz [OutputCache element for buforowanie (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228124(v=vs.100)).  
  
 ASP.NET umożliwia rozszerzoną buforowanie danych wyjściowych przez tworzenie niestandardowych dostawców pamięci podręcznej. Za pomocą dostawców niestandardowych można przechowywać zawartość pamięci podręcznej przy użyciu innych urządzeń magazynujących, takich jak dyski, magazyn w chmurze i rozproszone bufory pamięci podręcznej. Aby utworzyć niestandardowego dostawcę wyjściowej pamięci podręcznej, należy utworzyć klasę pochodzącą z klasy <xref:System.Web.Caching.OutputCacheProvider> i skonfigurować aplikację tak, aby korzystała z niestandardowego dostawcy pamięci podręcznej wyjściowej.  
  
## <a name="caching-in-wcf-rest-services"></a>Buforowanie w usługach REST WCF  
 W przypadku usług WCF REST .NET Framework umożliwia korzystanie z deklaracyjnego buforowania danych wyjściowych, które jest dostępne w ASP.NET. Dzięki temu można buforować odpowiedzi z operacji usługi REST platformy WCF. Gdy użytkownik wysyła żądanie HTTP GET do usługi, która jest skonfigurowana do buforowania, ASP.NET wysyła ponownie buforowaną odpowiedź, a metoda usługi nie jest wywoływana. Po wygaśnięciu pamięci podręcznej, gdy użytkownik wyśle żądanie HTTP GET, wywoływana jest metoda usługi i odpowiedź zostanie ponownie zbuforowana.  
  
 .NET Framework również umożliwia wdrożenie warunkowego buforowania HTTP GET. W przypadku scenariuszy REST warunkowe żądanie HTTP GET jest często używane przez usługi do implementowania inteligentnego buforowania HTTP zgodnie z opisem w [specyfikacji protokołu HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html). Aby uzyskać więcej informacji, zobacz [buforowanie obsługi usług HTTP sieci Web w programie WCF](../wcf/feature-details/caching-support-for-wcf-web-http-services.md).  
  
## <a name="extending-caching-in-the-net-framework"></a>Rozszerzanie buforowania w .NET Framework  
 Buforowanie w .NET Framework zostało zaprojektowane do rozszerzalności. Klasa <xref:System.Runtime.Caching.ObjectCache> umożliwia utworzenie niestandardowej implementacji pamięci podręcznej. Ta klasa zawiera elementy członkowskie, które są dostępne dla wszystkich zarządzanych aplikacji, w tym Windows Forms, Windows Presentation Foundation (WPF) i Windows Communications Foundation (WCF). Można to zrobić, aby utworzyć klasę pamięci podręcznej, która korzysta z innego mechanizmu magazynu, lub jeśli chcesz uzyskać szczegółową kontrolę nad operacjami pamięci podręcznej.  
  
 Aby zwiększyć pamięć podręczną, można wykonać następujące czynności:  
  
- Utwórz klasę niestandardową, która dziedziczy z klasy <xref:System.Runtime.Caching.ObjectCache>, a następnie podaj implementację niestandardowej pamięci podręcznej w klasie pochodnej.  
  
- Utwórz klasę pochodzącą z klasy <xref:System.Runtime.Caching.MemoryCache> i Dostosuj lub rozwiń klasę pochodną. Aby zapoznać się z przykładem, zobacz [buforowanie danych aplikacji przy użyciu wielu obiektów pamięci podręcznej w aplikacji ASP.NET](https://docs.microsoft.com/archive/blogs/aspnetue/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application).  
  
- Utwórz klasę pochodzącą z klasy <xref:System.Web.Caching.OutputCacheProvider> i skonfiguruj aplikację tak, aby korzystała z niestandardowego dostawcy wyjściowej pamięci podręcznej.  
  
 Aby uzyskać więcej informacji, zobacz temat [buforowanie danych wyjściowych w systemie ASP.NET 4 (w programie VS 2010 i .net 4,0 Series)](https://weblogs.asp.net/scottgu/extensible-output-caching-with-asp-net-4-vs-2010-and-net-4-0-series) na blogu Scott Guthrie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF](../wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [Przewodnik: buforowanie danych aplikacji w ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))
