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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49708175f8501c735a77b0f7f965a106b6e086f2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47424457"
---
# <a name="types-of-isolation"></a>Typy izolacji
Dostęp do wydzielonej pamięci masowej zawsze jest ograniczony do użytkownika, który go utworzył. Wdrożenie tego typu izolacji, środowisko uruchomieniowe języka wspólnego używa tego samego pojęcia tożsamości użytkownika, który rozpoznaje systemu operacyjnego, czyli tożsamość skojarzoną z procesem, w którym wykonywany jest kod, gdy jest otwierany magazyn. Ta tożsamość jest tożsamość uwierzytelnionego użytkownika, ale personifikacji może spowodować, że tożsamość bieżącego użytkownika, aby zmienić dynamicznie.  
  
 Dostęp do wydzielonej pamięci masowej jest także ograniczona zgodnie z tożsamością skojarzonego z domeny i zestawu aplikacji lub z samego zestawu. Środowisko uruchomieniowe uzyskuje tych tożsamości w następujący sposób:  
  
-   Tożsamość domeny reprezentuje dowód aplikacji, w przypadku aplikacji sieci web może być pełny adres URL. Kod, hostowany przez powłokę tożsamość domeny może opierać się na ścieżce katalogu aplikacji. Na przykład jeśli plik wykonywalny jest uruchomiony przy użyciu ścieżki C:\Office\MyApp.exe, tożsamość domeny będzie C:\Office\MyApp.exe.  
  
-   Tożsamość zestawu jest dowód zestawu. Obiekt może pochodzić z kryptograficznych podpis cyfrowy, który może być zestawu [silnej nazwy](../../../docs/framework/app-domains/strong-named-assemblies.md), wydawca oprogramowania zestawu lub jego tożsamość adresu URL. Jeśli zestaw ma silną nazwę i tożsamość wydawcy oprogramowania, używana jest tożsamość wydawcy oprogramowania. Jeśli zestaw pochodzi z Internetu i bez znaku, tożsamość adresu URL jest używana. Aby uzyskać więcej informacji na temat zestawów i silnych nazw, zobacz [programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
-   Przenieś magazynach mobilnych z użytkownikiem, który ma profil użytkownika mobilnego. Pliki są zapisywane w katalogu sieciowego i zostaną pobrane na dowolnym komputerze logują użytkownika. Aby uzyskać więcej informacji na temat profilów użytkowników mobilnych, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Łącząc pojęcia dotyczące użytkownika, domeny i tożsamość zestawu, wydzielonej pamięci masowej można odizolować dane w następujący sposób, z których każdy ma własny scenariusze użycia:  
  
-   [Izolacja według użytkownika i zestawu](#UserAssembly)  
  
-   [Izolacja według użytkownika, domeny i zestawu](#UserDomainAssembly)  
  
 Jedną z tych izolacji można łączyć z profilu użytkownika mobilnego. Aby uzyskać więcej informacji, zobacz sekcję [izolowany magazyn i Roaming](#Roaming).  
  
 Poniższa ilustracja przedstawia, jak magazyny są izolowane w różnych zakresach.  
  
 ![Izolacja według użytkownika i zestawu](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
Typy wydzielonej pamięci masowej  
  
 Należy zauważyć, że z wyjątkiem roamingu magazynów, wydzielona pamięć masowa jest zawsze niejawnie izolowane przez komputer ponieważ używa ona magazynów, które są lokalne dla danego komputera.  
  
> [!IMPORTANT]
>  Wydzielona pamięć masowa nie jest dostępna dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Zamiast tego należy użyć klas danych aplikacji w `Windows.Storage` uwzględnione w przestrzeni nazw [!INCLUDE[wrt](../../../includes/wrt-md.md)] interfejsu API, aby przechować lokalne dane i pliki. Aby uzyskać więcej informacji, zobacz [dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) w Centrum deweloperów Windows.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Izolacja według użytkownika i zestawu  
 Gdy zestaw, który używa tych danych są przechowywane musi być dostępna z dowolnej aplikacji domeny, izolacja według użytkownika i zestawu jest odpowiednie. Zazwyczaj w takiej sytuacji wydzielonej pamięci masowej służy do przechowywania danych, które mają zastosowanie dla wielu aplikacji i nie jest związany z określonej aplikacji, takie jak nazwa użytkownika lub informacje o licencji. Dostęp do magazynu izolowanego według użytkowników i zestaw, kod musi być zaufany w celu przekazywania informacji między aplikacjami. Zazwyczaj Izolacja według użytkownika i zestawu jest dozwolona w intranecie, ale nie w Internecie. Wywołanie metody statyczne <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> metody i przekazywanie przez użytkownika i zestawu <xref:System.IO.IsolatedStorage.IsolatedStorageScope> zwraca magazynu przy użyciu tego rodzaju izolacji.  
  
 Poniższy przykładowy kod pobiera magazynu, który jest izolowany dla konkretnego użytkownika i zestawu. Magazyn jest możliwy za pośrednictwem `isoFile` obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Na przykład, który korzysta z parametrów dowód, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Metoda jest dostępny jako skrót, jak pokazano w poniższym przykładzie kodu. Ten skrót, nie można otworzyć magazynów, które są w stanie mobilnych; Użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> w takich przypadkach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Izolacja według użytkownika, domeny i zestawu  
 Jeśli aplikacja korzysta z zestawu innych firm, który wymaga magazynu danych prywatnych, można użyć wydzielonej pamięci masowej do przechowywania danych prywatnych. Izolacja według użytkownika, domeny i zestawu zapewnia, że tylko kod w danym zestawie mogą uzyskiwać dostęp do danych i tylko wtedy, gdy zestaw jest używany przez aplikację, która była uruchomiona, gdy zestaw utworzony magazyn, a tylko wtedy, gdy użytkownik, dla którego został utworzony magazyn uruchamia  aplikacja. Izolacja według użytkownika, domeny i zestawu przechowuje zestawu innej firmy przed wyciekiem danych do innych aplikacji. Ten typ izolacji powinna być dowolnie domyślne, jeśli wiesz, aby używać wydzielonej pamięci masowej, ale nie pewności, jakiego typu izolacji używanych. Wywołanie metody statyczne <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile> i przekazując użytkownika, domeny i zestawu <xref:System.IO.IsolatedStorage.IsolatedStorageScope> zwraca magazynu przy użyciu tego rodzaju izolacji.  
  
 Poniższy przykładowy kod pobiera magazynu izolowanego według użytkownika, domeny i zestawu. Magazyn jest możliwy za pośrednictwem `isoFile` obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Inną metodą jest dostępny jako skrót, jak pokazano w poniższym przykładzie kodu. Ten skrót, nie można otworzyć magazynów, które są w stanie mobilnych; Użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> w takich przypadkach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Izolowany magazyn i roaming  
 Profile użytkowników mobilnych są funkcją Windows, która pozwala użytkownikowi na Ustawianie tożsamości w sieci i Użyj tej tożsamości do logowania się na każdym komputerze w sieci, przeniesienie wszystkich spersonalizowanych ustawień. Zestaw, który używa wydzielonej pamięci masowej można określić, że wydzielonej pamięci masowej przez użytkownika, należy przenieść z profilu mobilnego użytkownika. Roaming może służyć w połączeniu z izolacją Izolacja według użytkownika i zestawu lub przez użytkownika, domeny i zestawu. Jeżeli nie zastosowano zakres mobilnego, magazyny nie "wędrują" nawet, jeśli jest używany profil użytkownika mobilnego.  
  
 Poniższy przykładowy kod pobiera mobilnego magazynu izolowanego według użytkownika i zestawu. Magazyn jest możliwy za pośrednictwem `isoFile` obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Zakresu domeny można dodać do utworzenia mobilnego magazynu izolowanego według użytkownika, domeny i aplikacji. Poniższy przykład kodu pokazuje to.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
