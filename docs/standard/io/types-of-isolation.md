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
ms.openlocfilehash: 323b3fedb570ff97012b148aaeda2311b01960b5
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205021"
---
# <a name="types-of-isolation"></a>Typy izolacji
Dostęp do wydzielonej pamięci masowej jest zawsze ograniczony do użytkownika, który go utworzył. W celu zaimplementowania tego typu izolacji środowisko uruchomieniowe języka wspólnego używa tego samego pojęcia tożsamości użytkownika, która jest rozpoznawana przez system operacyjny, co jest tożsamością skojarzoną z procesem, w którym uruchomiono kod w momencie otwarcia magazynu. Ta tożsamość jest uwierzytelnianą tożsamością użytkownika, ale personifikacja może spowodować dynamiczną zmianę tożsamości bieżącego użytkownika.  
  
 Dostęp do izolowanego magazynu jest również ograniczany zgodnie z tożsamością skojarzoną z domeną i zestawem aplikacji albo z samym zestawem. Środowisko uruchomieniowe uzyskuje te tożsamości w następujący sposób:  
  
- Tożsamość domeny reprezentuje dowód aplikacji, co w przypadku, gdy aplikacja sieci Web może być pełnym adresem URL. W przypadku kodu hostowanego przez powłokę tożsamość domeny może opierać się na ścieżce katalogu aplikacji. Na przykład jeśli plik wykonywalny jest uruchamiany ze ścieżki C:\Office\MyApp.exe, tożsamość domeny byłaby C:\Office\MyApp.exe.  
  
- Tożsamość zestawu jest dowodem zestawu. Może to wynikać z kryptograficznego podpisu cyfrowego, który może być [silną nazwą](../assembly/strong-named.md)zestawu, wydawcą oprogramowania zestawu lub TOŻSAMOŚCIĄ adresu URL. Jeśli zestaw ma silną nazwę i tożsamość wydawcy oprogramowania, używana jest tożsamość wydawcy oprogramowania. Jeśli zestaw pochodzi z Internetu i jest niepodpisany, zostanie użyta tożsamość adresu URL. Aby uzyskać więcej informacji o zestawach i silnych nazwach, zobacz [programowanie z zestawami](../assembly/program.md).  
  
- Magazyny mobilne są przenoszone przy użyciu użytkownika, który ma profil użytkownika mobilnego. Pliki są zapisywane w katalogu sieciowym i pobierane na każdy komputer, na którym loguje się użytkownik. Aby uzyskać więcej informacji o profilach użytkowników mobilnych, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Łącząc koncepcje użytkownika, domeny i zestawu, izolowany magazyn może izolować dane w następujący sposób, z których każdy ma własne scenariusze użycia:  
  
- [Izolacja według użytkownika i zestawu](#UserAssembly)  
  
- [Izolacja według użytkownika, domeny i zestawu](#UserDomainAssembly)  
  
 Każdą z tych izolacji można połączyć z profilem użytkownika mobilnego. Aby uzyskać więcej informacji, zapoznaj się z sekcją [izolowanego magazynu i roamingu](#Roaming).  
  
 Na poniższej ilustracji przedstawiono sposób odizolowania magazynów w różnych zakresach:  
  
 ![Diagram, który pokazuje izolację według użytkownika i zestawu.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 Należy pamiętać, że z wyjątkiem magazynów mobilnych magazyn izolowany jest zawsze niejawnie izolowany przez komputer, ponieważ używa miejsc magazynu lokalnych dla danego komputera.  
  
> [!IMPORTANT]
> Izolowany magazyn nie jest dostępny dla aplikacji ze sklepu Windows 8. x. Zamiast tego należy użyć klas danych aplikacji znajdujących się w `Windows.Storage` przestrzenie nazw, które znajdują się w interfejsie API środowisko wykonawcze systemu Windows do przechowywania lokalnych danych i plików. Aby uzyskać więcej informacji, zobacz [dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) w centrum deweloperów systemu Windows.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Izolacja według użytkownika i zestawu  
 Gdy zestaw, który korzysta z magazynu danych, musi być dostępny z poziomu domeny dowolnej aplikacji, należy poizolować Izolacja według użytkownika i zestawu. Zwykle w takiej sytuacji magazyn izolowany jest używany do przechowywania danych, które są stosowane w wielu aplikacjach i nie jest powiązany z żadną określoną aplikacją, taką jak nazwa użytkownika lub informacje o licencji. Aby uzyskać dostęp do magazynu izolowanego przez użytkownika i zestaw, kod musi być zaufany, aby można było przesyłać informacje między aplikacjami. Zwykle Izolacja według użytkownika i zestawu jest dozwolona w intranecie, ale nie w Internecie. Wywołanie statycznej metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> i przekazanie do użytkownika i zestawu <xref:System.IO.IsolatedStorage.IsolatedStorageScope> zwraca magazyn z tym rodzajem izolacji.  
  
 Poniższy przykład kodu pobiera magazyn izolowany przez użytkownika i zestaw. Dostęp do magazynu można uzyskać za pomocą obiektu `isoFile`.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Aby zapoznać się z przykładem, który korzysta z parametrów dowodowych, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> jest dostępna jako skrót, jak pokazano w poniższym przykładzie kodu. Ten skrót nie może być używany do otwierania magazynów, które mogą być mobilne; w takich przypadkach należy używać <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Izolacja według użytkownika, domeny i zestawu  
 Jeśli aplikacja używa zestawu innej firmy, który wymaga prywatnego magazynu danych, można używać wydzielonej pamięci masowej do przechowywania danych prywatnych. Izolacja według użytkownika, domeny i zestawu zapewnia, że tylko kod w danym zestawie może uzyskać dostęp do danych i tylko wtedy, gdy zestaw jest używany przez aplikację, która była uruchomiona, gdy zestaw utworzył magazyn, i tylko wtedy, gdy użytkownik, dla którego utworzono ten magazyn, uruchamia  Aplikacja. Izolacja według użytkownika, domeny i zestawu utrzymuje zestaw innej firmy z powodu przecieku danych do innych aplikacji. Ten typ izolacji powinien być wyborem domyślnym, Jeśli wiesz, że chcesz użyć izolowanego magazynu, ale nie masz pewności, jakiego typu izolacji użyć. Wywołanie statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile> i przekazanie do użytkownika, domeny i zestawu <xref:System.IO.IsolatedStorage.IsolatedStorageScope> zwraca magazyn z tym rodzajem izolacji.  
  
 Poniższy przykład kodu pobiera magazyn izolowany według użytkownika, domeny i zestawu. Dostęp do magazynu można uzyskać za pomocą obiektu `isoFile`.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Inna metoda jest dostępna jako skrót, jak pokazano w poniższym przykładzie kodu. Ten skrót nie może być używany do otwierania magazynów, które mogą być mobilne; w takich przypadkach należy używać <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Izolowany magazyn i roaming  
 Profile użytkowników mobilnych to funkcja systemu Windows, która umożliwia użytkownikowi skonfigurowanie tożsamości w sieci i użycie tej tożsamości do logowania się do dowolnego komputera sieciowego i przechodzenia do wszystkich spersonalizowanych ustawień. Zestaw, który używa wydzielonej pamięci masowej, może określić, że magazyn izolowany użytkownika powinien być przenoszony przy użyciu profilu użytkownika mobilnego. Roaming może być używany w połączeniu z izolacją użytkownika i zestawu lub z izolacją według użytkownika, domeny i zestawu. Jeśli zakres roamingu nie jest używany, sklepy nie przechodzą nawet wtedy, gdy zostanie użyty profil użytkownika mobilnego.  
  
 Poniższy przykład kodu pobiera magazyn mobilny izolowany przez użytkownika i zestaw. Dostęp do magazynu można uzyskać za pomocą obiektu `isoFile`.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Zakres domeny można dodać, aby utworzyć magazyn roamingu izolowany przez użytkownika, domenę i aplikację. Poniższy przykład kodu demonstruje ten sposób.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
