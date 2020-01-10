---
title: 'Porady: usuwanie danych z izolowanego magazynu'
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
ms.openlocfilehash: 6b1e8e651fd8e18c79dd629c154fb6c4d74243e3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707830"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Porady: usuwanie danych z izolowanego magazynu
Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile> udostępnia dwie metody usuwania izolowanych plików magazynu:  
  
- Metoda wystąpienia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nie przyjmuje żadnych argumentów i usuwa magazyn, który go wywołuje. Dla tej operacji nie są wymagane żadne uprawnienia. Każdy kod, który może uzyskać dostęp do sklepu, może usunąć wszystkie lub wszystkie znajdujące się w nim dane.  
  
- Metoda statyczna <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> Pobiera wartość wyliczenia <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> i usuwa wszystkie magazyny dla użytkownika, który uruchomił kod. Ta operacja wymaga uprawnień <xref:System.Security.Permissions.IsolatedStorageFilePermission> do wartości <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie metod statycznych i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> wystąpień. Klasa uzyskuje dwa magazyny; jeden jest izolowany dla użytkownika i zestawu, a drugi jest izolowany dla użytkownika, domeny i zestawu. Użytkownik, domena i magazyn zestawów są następnie usuwane przez wywołanie metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> `isoStore1`pliku magazynu izolowanego. Następnie wszystkie pozostałe magazyny dla użytkownika są usuwane przez wywołanie metody statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
