---
title: Typy izolacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
ms.openlocfilehash: d85625b99603c0bd81346cf2076b8efe0e1bba42
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523888"
---
# <a name="types-of-isolation"></a>Typy izolacji
Dostęp do izolowanego magazynu jest zawsze ograniczony do użytkownika, który go utworzył. Aby zaimplementować ten typ izolacji, środowisko uruchomieniowe języka wspólnego używa tego samego pojęcia tożsamości użytkownika, które rozpoznaje system operacyjny, który jest tożsamością skojarzoną z procesem, w którym kod jest uruchomiony po otwarciu magazynu. Ta tożsamość jest uwierzytelnioną tożsamością użytkownika, ale personifikacja może spowodować dynamiczną zmianę tożsamości bieżącego użytkownika.  
  
 Dostęp do magazynu izolowanego jest również ograniczony zgodnie z tożsamością skojarzoną z domeną i zestawem aplikacji lub z samym zestawem. Środowisko wykonawcze uzyskuje te tożsamości w następujący sposób:  
  
- Tożsamość domeny reprezentuje dowód aplikacji, która w przypadku aplikacji sieci web może być pełny adres URL. W przypadku kodu hostowanego w powłoki tożsamość domeny może być oparta na ścieżce katalogu aplikacji. Jeśli na przykład plik wykonywalny jest uruchamiany ze ścieżki C:\Office\MyApp.exe, tożsamością domeny będzie C:\Office\MyApp.exe.  
  
- Tożsamość zestawu jest dowodem zestawu. Może to pochodzić z kryptograficznego podpisu cyfrowego, który może być [silną nazwą](../assembly/strong-named.md)zestawu, wydawcą oprogramowania zestawu lub jego tożsamością adresu URL. Jeśli zestaw ma zarówno silną nazwę, jak i tożsamość wydawcy oprogramowania, używana jest tożsamość wydawcy oprogramowania. Jeśli zestaw pochodzi z Internetu i jest niepodpisany, używana jest tożsamość adresu URL. Aby uzyskać więcej informacji na temat zestawów i silnych nazw, zobacz [Programowanie za pomocą zestawów](/dotnet/standard/assembly/index).  
  
- Mobilne sklepy są przesuwne z użytkownikiem, który ma mobilny profil użytkownika. Pliki są zapisywane w katalogu sieciowym i są pobierane na dowolny komputer, na który użytkownik się loguje. Aby uzyskać więcej informacji na <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>temat mobilnych profili użytkowników, zobacz .  
  
 Łącząc pojęcia tożsamości użytkownika, domeny i zestawu, izolowany magazyn może izolować dane w następujący sposób, z których każdy ma własne scenariusze użycia:  
  
- [Izolacja według użytkownika i zespołu](#UserAssembly)  
  
- [Izolacja według użytkownika, domeny i zestawu](#UserDomainAssembly)  
  
 Każda z tych izolacji można połączyć z mobilnym profilem użytkownika. Aby uzyskać więcej informacji, zobacz sekcję [Izolowane magazynowanie i roaming](#Roaming).  
  
 Na poniższej ilustracji pokazano, jak magazyny są izolowane w różnych zakresach:  
  
 ![Diagram, który pokazuje izolację według użytkownika i zestawu.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 Należy zauważyć, że z wyjątkiem magazynów mobilnych izolowane magazynu jest zawsze niejawnie izolowane przez komputer, ponieważ używa obiektów magazynu, które są lokalne dla danego komputera.  
  
> [!IMPORTANT]
> Magazyn izolowany nie jest dostępny dla aplikacji ze Sklepu Windows 8.x. Zamiast tego należy użyć klas `Windows.Storage` danych aplikacji w obszarach nazw zawartych w interfejsie API środowiska wykonawczego systemu Windows do przechowywania danych i plików lokalnych. Aby uzyskać więcej informacji, zobacz [Dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) w Centrum deweloperów systemu Windows.  
  
<a name="UserAssembly"></a>
## <a name="isolation-by-user-and-assembly"></a>Izolacja według użytkownika i zestawu  
 Gdy zestaw, który używa magazynu danych musi być dostępny z domeny dowolnej aplikacji, izolacja według użytkownika i zestawu jest odpowiedni. Zazwyczaj w tej sytuacji izolowany magazyn jest używany do przechowywania danych, które mają zastosowanie w wielu aplikacjach i nie jest powiązany z żadną konkretną aplikacją, taką jak nazwa użytkownika lub informacje o licencji. Aby uzyskać dostęp do magazynu izolowane przez użytkownika i zestawu, kod musi być zaufany do przesyłania informacji między aplikacjami. Zazwyczaj izolacja według użytkownika i zestawu jest dozwolona w intranetach, ale nie w Internecie. Wywołanie metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> statycznej i przekazywanie <xref:System.IO.IsolatedStorage.IsolatedStorageScope> w użytkowniku i zestawu zwraca magazyn z tego rodzaju izolacji.  
  
 Poniższy przykład kodu pobiera magazyn, który jest izolowany przez użytkownika i zestawu. Dostęp do magazynu można `isoFile` uzyskać za pośrednictwem obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Na przykład, który używa parametrów <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>dowodów, zobacz .  
  
 Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> jest dostępna jako skrót, jak pokazano w poniższym przykładzie kodu. Tego skrótu nie można użyć do otwierania magazynów, które są w stanie roamingu; w <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> takich przypadkach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>
## <a name="isolation-by-user-domain-and-assembly"></a>Izolacja według użytkownika, domeny i zestawu  
 Jeśli aplikacja używa zestawu innej firmy, który wymaga prywatnego magazynu danych, można użyć magazynu izolowanego do przechowywania danych prywatnych. Izolacja według użytkownika, domeny i zestawu zapewnia, że tylko kod w danym zestawie może uzyskać dostęp do danych i tylko wtedy, gdy zestaw jest używany przez aplikację, która była uruchomiona podczas zestawu utworzonego magazynu i tylko wtedy, gdy użytkownik, dla którego utworzono magazyn, uruchamia aplikację. Izolacja według użytkownika, domeny i zestawu chroni zespół innych firm przed wyciekiem danych do innych aplikacji. Ten typ izolacji powinien być domyślnym wyborem, jeśli wiesz, że chcesz użyć izolowanego magazynu, ale nie masz pewności, jakiego typu izolacji użyć. Wywołanie metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile> i przekazywania w użytkowniku, domeny i zestawu <xref:System.IO.IsolatedStorage.IsolatedStorageScope> zwraca magazyn z tego rodzaju izolacji.  
  
 Poniższy przykład kodu pobiera magazyn izolowane przez użytkownika, domeny i zestawu. Dostęp do magazynu można `isoFile` uzyskać za pośrednictwem obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Inna metoda jest dostępna jako skrót, jak pokazano w poniższym przykładzie kodu. Tego skrótu nie można użyć do otwierania magazynów, które są w stanie roamingu; w <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> takich przypadkach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>
## <a name="isolated-storage-and-roaming"></a>Izolowany magazyn i roaming  
 Mobilne profile użytkowników to funkcja systemu Windows, która umożliwia użytkownikowi skonfigurowanie tożsamości w sieci i użycie tej tożsamości do zalogowania się do dowolnego komputera sieciowego, przenosząc wszystkie spersonalizowane ustawienia. Zestaw, który używa magazynu izolowanego można określić, że izolowane magazynu użytkownika powinny być przesunięte z profilu użytkownika mobilnego. Roaming może być używany w połączeniu z izolacją przez użytkownika i zestawu lub z izolacją przez użytkownika, domeny i zestawu. Jeśli zakres roamingu nie jest używany, sklepy nie będą się przemieszczać, nawet jeśli używany jest mobilny profil użytkownika.  
  
 Poniższy przykład kodu pobiera magazyn mobilny izolowane przez użytkownika i zestawu. Dostęp do magazynu można `isoFile` uzyskać za pośrednictwem obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Zakres domeny można dodać, aby utworzyć magazyn mobilny izolowane przez użytkownika, domeny i aplikacji. Poniższy przykład kodu pokazuje to.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
