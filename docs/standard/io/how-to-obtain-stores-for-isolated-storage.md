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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 604aabbff8554416d6794ff0b87188fb5bcc3185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576685"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Porady: uzyskiwanie magazynów dla izolowanego magazynu
Izolowane store ujawnia wirtualnym systemie plików w ramach przedziału danych. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Klasa zapewnia kilka metod do interakcji z magazynu izolowanego. Aby utworzyć i pobrać magazynów, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> oferuje trzy metody statycznej:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Zwraca magazynu, która jest odizolowana przez użytkownika i zestawu.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> Zwraca magazynu, który jest izolowana domena i zestawu.  
  
     Obie metody pobrać sklepu, która należy do kodu, w którym są one nazywane.  
  
-   Statyczna metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> zwraca izolowanego magazynu, określonej przez przekazywanie kombinacją parametrów zakresu.  
  
 Poniższy kod zwraca sklepu, która jest odizolowana przez użytkownika, zestawu i domeny.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Można użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metodę, aby określić, że magazyn powinno mieć Roaming z profilu użytkownika mobilnego. Aby uzyskać więcej informacji na temat tej konfiguracji, zobacz [typy izolacji](../../../docs/standard/io/types-of-isolation.md).  
  
 Izolowanych magazynów uzyskana w ramach różnych zestawów są domyślnie w sklepach. Są dostępne w magazynie różnych zestawów lub domen przez przekazywanie w dowód zestawów lub domen w parametrach <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. Wymaga to uprawnień dostępu do izolowanego magazynu za tożsamość domeny aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> przeciążenia metody.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, I <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody zwracają <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektu. Aby określić, jakiego typu izolacji jest najbardziej odpowiednia w danej sytuacji, zobacz [typy izolacji](../../../docs/standard/io/types-of-isolation.md). Jeśli masz obiektu pliku izolowanego magazynu można użyć metod izolowanych magazynów Odczyt, zapis, tworzenie i usuwanie plików i katalogów.  
  
 Nie istnieje mechanizm uniemożliwiający kodu przekazywanie <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiekt do kodu, który nie ma wystarczające prawa dostępu do pobrania samego magazynu. Domeny i zestawu tożsamości i uprawnienia izolowanych magazynów są sprawdzane tylko wtedy, gdy odwołanie do <xref:System.IO.IsolatedStorage.IsolatedStorage> obiektu są uzyskiwane, zwykle w <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. Odwołania do ochrony <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, w związku z tym obowiązkiem jest kod, który używa tych odwołań.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zapewnia prosty przykład klasy uzyskiwania sklepu, która jest odizolowana przez użytkownika i zestawu. Można zmienić kod można pobrać ze sklepu, która jest odizolowana przez użytkownika, domena i zestawu przez dodanie <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> do argumentów który <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> przekazuje metody.  
  
 Po uruchomieniu kodu, możesz sprawdzić, czy magazyn został utworzony przez wpisanie **/list StoreAdm** w wierszu polecenia. Ta funkcja jest uruchamiana [narzędzie izolowanych magazynów (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) i zawiera wszystkie bieżące izolowane magazynów dla użytkownika.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)  
 [Typy izolacji](../../../docs/standard/io/types-of-isolation.md)  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
