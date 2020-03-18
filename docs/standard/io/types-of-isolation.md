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
ms.openlocfilehash: 99e1f3f96465d05c100a0dbb2bc5218810c33754
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159432"
---
# <a name="types-of-isolation"></a>Typy izolacji
Dostęp do izolowanego magazynu jest zawsze ograniczony do użytkownika, który go utworzył. Aby zaimplementować ten typ izolacji, środowisko uruchomieniowe języka wspólnego używa tego samego pojęcia tożsamości użytkownika, który rozpoznaje system operacyjny, który jest tożsamością skojarzoną z procesem, w którym kod jest uruchomiony podczas otwierania magazynu. Ta tożsamość jest uwierzytelnioną tożsamością użytkownika, ale personifikacja może spowodować dynamiczną zmianę tożsamości bieżącego użytkownika.  
  
 Dostęp do izolowanego magazynu jest również ograniczony zgodnie z tożsamością skojarzoną z domeną i zestawem aplikacji lub tylko z zestawem. Program runtime uzyskuje te tożsamości w następujący sposób:  
  
- Tożsamość domeny reprezentuje dowody aplikacji, która w przypadku aplikacji sieci web może być pełny adres URL. W przypadku kodu hostowanego przez powłokę tożsamość domeny może być oparta na ścieżce katalogu aplikacji. Na przykład jeśli plik wykonywalny działa ze ścieżki C:\Office\Mojaaplikacja.exe, tożsamościdomeny będzie C:\Office\MyApp.exe.  
  
- Tożsamość zestawu jest dowodem zestawu. Może to pochodzić z kryptograficznego podpisu cyfrowego, który może być [silną nazwą](../assembly/strong-named.md)zestawu, wydawcą oprogramowania zestawu lub jego tożsamością adresu URL. Jeśli zestaw ma zarówno silną nazwę, jak i tożsamość wydawcy oprogramowania, używana jest tożsamość wydawcy oprogramowania. Jeśli zestaw pochodzi z Internetu i jest niepodpisany, używana jest tożsamość adresu URL. Aby uzyskać więcej informacji na temat zestawów i silnych nazw, zobacz [Programowanie z zestawami](../assembly/program.md).  
  
- Magazyny mobilne są przenoszeni echem u użytkownika, który ma mobilny profil użytkownika. Pliki są zapisywane w katalogu sieciowym i pobierane na dowolny komputer, do którego użytkownik się loguje. Aby uzyskać więcej informacji na <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>temat mobilnych profili użytkowników, zobacz .  
  
 Łącząc pojęcia tożsamości użytkownika, domeny i zestawu, izolowany magazyn może izolować dane w następujący sposób, z których każdy ma własne scenariusze użycia:  
  
- [Izolacja według użytkownika i złożenia](#UserAssembly)  
  
- [Izolacja według użytkownika, domeny i zestawu](#UserDomainAssembly)  
  
 Jedną z tych izolacji można łączyć z mobilnym profilem użytkownika. Aby uzyskać więcej informacji, zobacz sekcję [Izolowane magazynu i roamingu](#Roaming).  
  
 Na poniższej ilustracji pokazano, jak magazyny są izolowane w różnych zakresach:  
  
 ![Diagram, który pokazuje izolację przez użytkownika i zestawu.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 Należy zauważyć, że z wyjątkiem magazynów mobilnych izolowany magazyn jest zawsze niejawnie izolowany przez komputer, ponieważ używa magazynów, które są lokalne dla danego komputera.  
  
> [!IMPORTANT]
> Izolowana pamięć nie jest dostępna dla aplikacji ze Sklepu Windows 8.x. Zamiast tego użyj klas danych `Windows.Storage` aplikacji w przestrzeniach nazw zawartych w interfejsie API środowiska uruchomieniowego systemu Windows do przechowywania danych lokalnych i plików. Aby uzyskać więcej informacji, zobacz [Dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) w Centrum deweloperów systemu Windows.  
  
<a name="UserAssembly"></a>
## <a name="isolation-by-user-and-assembly"></a>Izolacja według użytkownika i zestawu  
 Gdy zestaw, który używa magazynu danych musi być dostępny z domeny dowolnej aplikacji, izolacja przez użytkownika i zestawu jest właściwe. Zazwyczaj w tej sytuacji izolowany magazyn jest używany do przechowywania danych, które mają zastosowanie w wielu aplikacjach i nie jest powiązany z żadnej określonej aplikacji, takich jak nazwa użytkownika lub informacje o licencji. Aby uzyskać dostęp do magazynu izolowanego przez użytkownika i zestawu, kod musi być zaufany do przesyłania informacji między aplikacjami. Zazwyczaj izolacja przez użytkownika i zestawu jest dozwolone w intranecie, ale nie w Internecie. Wywołanie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> metody statycznej i przekazywanie <xref:System.IO.IsolatedStorage.IsolatedStorageScope> w użytkownika i zestawu zwraca magazyn z tego rodzaju izolacji.  
  
 Poniższy przykład kodu pobiera magazyn, który jest izolowany przez użytkownika i zestawu. Dostęp do magazynu można `isoFile` uzyskać za pośrednictwem obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Na przykład, który używa parametrów <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>dowodów, zobacz .  
  
 Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> jest dostępna jako skrót, jak pokazano w poniższym przykładzie kodu. Ten skrót nie może służyć do otwierania sklepów, które są zdolne do roamingu; wykorzystania <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> w takich przypadkach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>
## <a name="isolation-by-user-domain-and-assembly"></a>Izolacja według użytkownika, domeny i zestawu  
 Jeśli aplikacja używa zestawu innej firmy, który wymaga magazynu prywatnych danych, można użyć izolowanego magazynu do przechowywania danych prywatnych. Izolacja według użytkownika, domeny i zestawu zapewnia, że tylko kod w danym zestawie może uzyskać dostęp do danych i tylko wtedy, gdy zestaw jest używany przez aplikację, która była uruchomiona, gdy zestaw utworzył magazyn, i tylko wtedy, gdy użytkownik, dla którego magazyn został utworzony uruchamia Aplikacji. Izolacja według użytkownika, domeny i zestawu chroni zestaw innych firm przed wyciekiem danych do innych aplikacji. Ten typ izolacji powinien być domyślnym wyborem, jeśli wiesz, że chcesz użyć izolowanego magazynu, ale nie masz pewności, jakiego typu izolacji użyć. Wywołanie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile> statycznej i przekazywanie w użytkowniku, domenie i zestaw <xref:System.IO.IsolatedStorage.IsolatedStorageScope> zwraca magazyn z tego rodzaju izolacji.  
  
 Poniższy przykład kodu pobiera magazyn izolowany przez użytkownika, domenę i zestaw. Dostęp do magazynu można `isoFile` uzyskać za pośrednictwem obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Inna metoda jest dostępna jako skrót, jak pokazano w poniższym przykładzie kodu. Ten skrót nie może służyć do otwierania sklepów, które są zdolne do roamingu; wykorzystania <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> w takich przypadkach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>
## <a name="isolated-storage-and-roaming"></a>Izolowany magazyn i roaming  
 Profile użytkowników mobilnych to funkcja systemu Windows, która umożliwia użytkownikowi konfigurowanie tożsamości w sieci i używanie tej tożsamości do logowania się do dowolnego komputera sieciowego, przenosząc wszystkie spersonalizowane ustawienia. Zestaw, który używa izolowanego magazynu można określić, że izolowany magazyn użytkownika powinien zostać przeniesiony z mobilnym profilem użytkownika. Roaming może być używany w połączeniu z izolacją według użytkownika i zestawu lub izolacji według użytkownika, domeny i zestawu. Jeśli zakres roamingu nie jest używany, sklepy nie będą się poruszać, nawet jeśli używany jest mobilny profil użytkownika.  
  
 Poniższy przykład kodu pobiera magazyn mobilny izolowany przez użytkownika i zestawu. Dostęp do magazynu można `isoFile` uzyskać za pośrednictwem obiektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Zakres domeny można dodać, aby utworzyć magazyn mobilny izolowany przez użytkownika, domenę i aplikację. Poniższy przykład kodu pokazuje to.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
