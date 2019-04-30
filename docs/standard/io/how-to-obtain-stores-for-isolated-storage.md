---
title: 'Instrukcje: Uzyskiwanie magazynów dla izolowanego magazynu'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0968443af28e2d403b08a1af50846e7a1369db49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751751"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Instrukcje: Uzyskiwanie magazynów dla izolowanego magazynu
Izolowanym magazynie udostępnia wirtualny system plików w ramach przedziału danych. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Klasa zapewnia szereg metod do interakcji z izolowanym magazynie. Tworzenie i pobieranie magazynów, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> udostępnia trzy metody statyczne:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Zwraca magazynu, który jest izolowany dla konkretnego użytkownika i zestawu.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> Zwraca magazynu, która jest odizolowana, domeny i zestawu.  
  
     Obie metody pobierania sklepu, która należy do kodu, z którego są wywoływane.  
  
- Metoda statyczna <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> zwraca izolowanym magazynie, który jest określony, przekazując kombinacji parametrów zakresu.  
  
 Poniższy kod zwraca magazynu, który jest izolowany dla konkretnego użytkownika, zestawu i domeny.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Możesz użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metodę, aby określić, czy Magazyn powinien są przekazywane przy użyciu profilu użytkownika mobilnego. Aby uzyskać więcej informacji na temat konfigurowania tego, zobacz [typy izolacji](../../../docs/standard/io/types-of-isolation.md).  
  
 Izolowanych magazynów uzyskany z w ramach różnych zestawów są domyślnie w różnych sklepach. Jest dostępne w magazynie do innego zestawu lub domeny, przekazując dowodu zestawu lub domeny w parametrach w <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. Wymaga to uprawnień do dostępu do wydzielonej pamięci masowej przez tożsamość w domenie aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> przeciążenia metody.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, I <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody zwracają <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektu. Aby ułatwić podjęcie decyzji, który typ izolacji jest najbardziej odpowiednia w danej sytuacji, zobacz [typy izolacji](../../../docs/standard/io/types-of-isolation.md). W przypadku obiektu pliku wydzielonej pamięci masowej można metody wydzielona pamięć masowa umożliwia odczyt, zapis, tworzenie i usuwanie plików i katalogów.  
  
 Nie ma mechanizmu uniemożliwiający przekazywanie kodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiekt, aby kod, który nie ma wystarczające uprawnienia dostępu, aby uzyskać samego magazynu. Domeny i zestawu tożsamości i uprawnień wydzielonej pamięci masowej są sprawdzane tylko wtedy, gdy odwołanie do <xref:System.IO.IsolatedStorage.IsolatedStorage> zostanie pobrany, zwykle w <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. Odwołania do ochrony <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, w związku z tym, obowiązkiem jest kod, który używa tych odwołań.  
  
## <a name="example"></a>Przykład  
 Poniższy kod stanowi prosty przykład klasy uzyskiwania w magazynie, który jest izolowany dla konkretnego użytkownika i zestawu. Kod można zmienić do pobrania w magazynie, który jest izolowany dla konkretnego użytkownika, domeny i zestawu, dodając <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> do argumentów, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda przebiegów.  
  
 Po uruchomieniu kodu, możesz sprawdzić, czy magazyn został utworzony, wpisując **/list StoreAdm** w wierszu polecenia. Spowoduje to uruchomienie [narzędzie wydzielonej pamięci masowej (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) i wyświetla wszystkie bieżące izolowany magazynów dla użytkownika.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
- [Typy izolacji](../../../docs/standard/io/types-of-isolation.md)
- [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
