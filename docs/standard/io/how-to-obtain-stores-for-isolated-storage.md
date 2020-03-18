---
title: 'Porady: uzyskiwanie magazynów dla izolowanego magazynu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
ms.openlocfilehash: 7104ba665f60c2d55217a2d8628c85f6e469ad6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706934"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Porady: uzyskiwanie magazynów dla izolowanego magazynu
Izolowany magazyn udostępnia wirtualny system plików w komorze danych. Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile> dostarcza szereg metod interakcji z izolowanym magazynie. Aby utworzyć i <xref:System.IO.IsolatedStorage.IsolatedStorageFile> pobrać magazyny, zawiera trzy metody statyczne:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>zwraca magazyn, który jest izolowany przez użytkownika i zestawu.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>zwraca magazyn, który jest izolowany przez domeny i zestawu.  
  
     Obie metody pobrać magazyn, który należy do kodu, z którego są wywoływane.  
  
- Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> statyczna zwraca izolowany magazyn, który jest określony przez przekazywanie w kombinacji parametrów zakresu.  
  
 Poniższy kod zwraca magazyn, który jest izolowany przez użytkownika, zestawu i domeny.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Można użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> tej metody, aby określić, że sklep powinien poruszać się z mobilnym profilem użytkownika. Aby uzyskać szczegółowe informacje na temat konfigurowania tej konfiguracji, zobacz [Typy izolacji](../../../docs/standard/io/types-of-isolation.md).  
  
 Izolowane magazyny uzyskane z różnych złożeń są domyślnie różnymi magazynami. Można uzyskać dostęp do magazynu innego zestawu lub domeny, przekazując w <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> zestawie lub dowody domeny w parametrach metody. Wymaga to uprawnień dostępu do izolowanego magazynu według tożsamości domeny aplikacji. Aby uzyskać więcej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> informacji, zobacz przeciążenia metody.  
  
 Polecenie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> i metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile> zwracają obiekt. Aby ułatwić podjęcie decyzji, który typ izolacji jest najbardziej odpowiedni dla twojej sytuacji, zobacz [Typy izolacji](../../../docs/standard/io/types-of-isolation.md). Jeśli masz izolowany obiekt pliku magazynu, można użyć izolowanych metod przechowywania do odczytu, zapisu, tworzenia i usuwania plików i katalogów.  
  
 Nie istnieje żaden mechanizm, który <xref:System.IO.IsolatedStorage.IsolatedStorageFile> uniemożliwia kod owijanie obiektu do kodu, który nie ma wystarczającego dostępu do uzyskania samego magazynu. Tożsamości domeny i zestawu oraz uprawnienia magazynu izolowanego są <xref:System.IO.IsolatedStorage.IsolatedStorage> sprawdzane tylko wtedy, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>gdy <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> uzyskuje się odwołanie do obiektu, zazwyczaj w , lub metody. Ochrona odwołań do <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów jest zatem odpowiedzialność kodu, który używa tych odwołań.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera prosty przykład klasy uzyskiwania magazynu, który jest izolowany przez użytkownika i zestawu. Kod można zmienić, aby pobrać magazyn, który jest izolowany <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> przez użytkownika, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> domeny i zestawu przez dodanie do argumentów, które przechodzi metoda.  
  
 Po uruchomieniu kodu można potwierdzić, że magazyn został utworzony przez wpisanie **storeAdm /LIST** w wierszu polecenia. Spowoduje to [uruchamianie narzędzia Izolowane magazynu (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) i wyświetla listę wszystkich bieżących izolowanych magazynów dla użytkownika.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
- [Typy izolacji](../../../docs/standard/io/types-of-isolation.md)
- [Zestawy w środowisku .NET](../assembly/index.md)
