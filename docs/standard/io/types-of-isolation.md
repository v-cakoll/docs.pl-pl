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
ms.openlocfilehash: c0c888181b5f2150c37a87957cd932e10a36f7f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577619"
---
# <a name="types-of-isolation"></a>Typy izolacji
Dostęp do magazynu izolowanego zawsze jest ograniczony do użytkownika, który go utworzył. Aby wdrożyć ten typ izolacji, środowisko uruchomieniowe języka wspólnego używa tego samego pojęcia tożsamości użytkownika, która rozpoznaje systemu operacyjnego, czyli tożsamość skojarzoną z procesem, w którym wykonywany jest kod po otwarciu Sklepu. Ta tożsamość jest tożsamość uwierzytelnionego użytkownika, ale personifikacji może spowodować tożsamości bieżącego użytkownika można zmienić dynamicznie.  
  
 Dostęp do magazynu izolowanego również jest ograniczony zgodnie z tożsamość skojarzoną z domeny aplikacji i zestawu lub samego zestawu. Środowisko uruchomieniowe uzyskuje tymi tożsamościami w następujący sposób:  
  
-   Tożsamość domeny reprezentuje świadectwo aplikacji, która w przypadku aplikacji sieci web może być pełny adres URL. Hostowana powłoki kodu tożsamość domeny może być oparta na ścieżkę katalogu aplikacji. Na przykład jeśli plik wykonywalny uruchamiany ze ścieżki C:\Office\MyApp.exe, tożsamość domeny będzie C:\Office\MyApp.exe.  
  
-   Tożsamość zestawu jest świadectwa zestawu. Obiekt może pochodzić z kryptograficznych podpis cyfrowy, który może być zestawu [silnej nazwy](../../../docs/framework/app-domains/strong-named-assemblies.md), wydawca oprogramowania zestaw lub jego tożsamość adresu URL. Jeśli zestaw ma silną nazwę i tożsamości wydawcy oprogramowania, używana jest tożsamość wydawcy oprogramowania. Jeśli zestaw jest dostarczany z Internetem i nie jest podpisany, używana jest tożsamość adresu URL. Aby uzyskać więcej informacji na temat zestawów i silne nazwy, zobacz [programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
-   Magazyny mobilnego przenieść z użytkownikiem, który ma mobilny profil użytkownika. Pliki są zapisywane w katalogu sieciowym i są pobierane na dowolnym komputerze użytkownik loguje się do. Aby uzyskać więcej informacji na temat profilów użytkowników mobilnych, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Łącząc pojęcia użytkownika, domena i tożsamości zestawu izolowanych magazynów można odizolować danych w następujący sposób, z których każdy ma własny scenariusze użycia:  
  
-   [Izolacja według użytkownika i zestawu](#UserAssembly)  
  
-   [Izolacja przez użytkownika, domena i zestawu](#UserDomainAssembly)  
  
 Jedną z tych izolacji można łączyć z profilu użytkownika mobilnego. Aby uzyskać więcej informacji, zobacz sekcję [izolowanych magazynów oraz mobilne](#Roaming).  
  
 Poniższa ilustracja przedstawia, jak magazyny są izolowane w innych zakresach.  
  
 ![Izolacja według użytkownika i zestawu](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
Typy izolowanego magazynu  
  
 Należy pamiętać, że z wyjątkiem roamingu magazynów, izolowanego magazynu jest zawsze niejawnie izolowana przez komputer ponieważ używa funkcji magazynu, które są lokalne dla danego komputera.  
  
> [!IMPORTANT]
>  Izolowany magazyn jest niedostępny dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Zamiast tego należy użyć klasy danych aplikacji w `Windows.Storage` obszary nazw dołączane w [!INCLUDE[wrt](../../../includes/wrt-md.md)] interfejsu API do przechowywania plików i danych lokalnych. Aby uzyskać więcej informacji, zobacz [danych aplikacji](/previous-versions/windows/apps/hh464917(v=win.10)) w Centrum deweloperów systemu Windows.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Izolacja według użytkownika i zestawu  
 Zestaw, który używa danych przechowywania musi być dostępny z domeny dowolnej aplikacji, izolacji użytkowników i zestawu jest odpowiedni. Zazwyczaj w takiej sytuacji izolowanego magazynu jest używany do przechowywania danych, które stosuje dla wielu aplikacji i nie jest związana z określonej aplikacji, takie jak nazwa użytkownika lub informacje o licencji. Dostęp do magazynu samodzielnie przez użytkownika i zestaw, kod musi być zaufany w celu przekazywania informacji między aplikacjami. Zazwyczaj izolacji użytkowników i zestawu jest dozwolona w sieci intranet, ale nie w Internecie. Podczas wywoływania statycznych <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> — metoda i przekazywanie przez użytkownika i zestaw <xref:System.IO.IsolatedStorage.IsolatedStorageScope> zwraca magazynu z tego typu izolacji.  
  
 Poniższy przykładowy kod pobiera sklepu, która jest odizolowana przez użytkownika i zestawu. Magazyn jest możliwy za pośrednictwem `isoFile` obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Na przykład, który korzysta z parametrów dowód, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Metoda jest dostępna jako skrót, jak pokazano w poniższym przykładzie kodu. Ten skrót nie może służyć do otwierania magazynów, które są w stanie mobilnego; Użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> w takich przypadkach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Izolacja według użytkownika, domeny i zestawu  
 Jeśli aplikacja korzysta z zestawu innej firmy, który wymaga magazynu danych, można użyć izolowanego magazynu do przechowywania danych prywatnych. Izolacja przez użytkownika, domena i zestawu zapewnia, że tylko kod w danym zestawie ma dostęp do danych i tylko wtedy, gdy zestaw jest używany przez aplikację, która była uruchomiona w chwili zestawu utworzony magazyn i tylko wtedy, gdy użytkownik, dla którego został utworzony magazyn działa  aplikacja. Izolacja przez użytkownika, domena i zestawu zachowuje zestawu innej firmy przed wyciekiem danych do innych aplikacji. Tego typu izolacji należy wybór domyślny, jeśli znasz chcesz używać izolowanego magazynu, ale nie pewności, jakiego typu izolacji do użycia. Podczas wywoływania statycznych <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile> i przekazując użytkownika, domena i zestawu <xref:System.IO.IsolatedStorage.IsolatedStorageScope> zwraca magazynu z tego typu izolacji.  
  
 Poniższy przykładowy kod pobiera sklepu samodzielnie przez użytkownika, domena i zestawu. Magazyn jest możliwy za pośrednictwem `isoFile` obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Inną metodą jest dostępna jako skrót, jak pokazano w poniższym przykładzie kodu. Ten skrót nie może służyć do otwierania magazynów, które są w stanie mobilnego; Użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> w takich przypadkach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Izolowany magazyn i roaming  
 Profile użytkowników mobilnych są funkcji systemu Windows, który umożliwia użytkownikowi skonfigurować tożsamości w sieci i używać tej tożsamości do zalogowania się do dowolnego komputera w sieci, przeniesienie wszystkich spersonalizowanych ustawień. Zestaw, który korzysta z magazynu izolowanego można określić, że izolowanych magazynów użytkownika należy przenieść z profilu mobilnego użytkownika. Roaming może służyć w połączeniu z funkcją izolowania użytkowników i zestawu lub przy użyciu izolacji przez użytkownika, domena i zestawu. Jeśli zakres mobilne nie jest używany, magazynów nie będzie są przekazywane nawet wtedy, gdy jest używany profil użytkownika mobilnego.  
  
 Poniższy przykładowy kod pobiera mobilnego sklepu samodzielnie przez użytkownika i zestawu. Magazyn jest możliwy za pośrednictwem `isoFile` obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Zakresu domeny można dodać do utworzenia magazynu mobilnego samodzielnie przez użytkownika, domena i aplikacji. W poniższym przykładzie kodu pokazano to.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
