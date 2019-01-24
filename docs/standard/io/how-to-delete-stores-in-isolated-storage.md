---
title: 'Instrukcje: Usuwanie magazynów w wydzielonej pamięci masowej'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19a671cac609e79088956ecb4324ebb0a25fb941
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547404"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Instrukcje: Usuwanie magazynów w wydzielonej pamięci masowej
<xref:System.IO.IsolatedStorage.IsolatedStorageFile> Klasa zapewnia dwie metody usuwania plików wydzielonej pamięci masowej:  
  
-   Metoda wystąpienia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nie przyjmuje żadnych argumentów, a następnie usuwa magazynu, który ją wywołuje. Nie uprawnienia są wymagane do wykonania tej operacji. Wszelki kod, który można uzyskać dostępu do magazynu można usunąć dowolnych lub wszystkich danych wewnątrz niego.  
  
-   Metoda statyczna <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartość wyliczenia i usuwa wszystkie magazyny dla użytkownika, który jest uruchomiony kod. Ta operacja wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnienia dla <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie statycznych i wystąpienia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metody. Klasa uzyskuje dwóch magazynów; jeden jest izolowane dla użytkownika i zestawu, a drugi to izolowane i użytkownika, domeny i zestawu. Magazyn użytkownika, domeny i zestawu jest usuwany przez wywołanie metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metoda pliku wydzielonej pamięci masowej `isoStore1`. Następnie wszystkie pozostałe magazyny użytkownika są usuwane przez wywołanie metody statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
