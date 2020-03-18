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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707830"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Porady: usuwanie danych z izolowanego magazynu
Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile> dostarcza dwie metody usuwania izolowanych plików magazynu:  
  
- Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> instance nie bierze żadnych argumentów i usuwa magazyn, który wywołuje go. Dla tej operacji nie są wymagane żadne uprawnienia. Każdy kod, który może uzyskać dostęp do magazynu można usunąć wszystkie lub wszystkie dane wewnątrz niego.  
  
- Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> statyczna <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> pobiera wartość wyliczenia i usuwa wszystkie magazyny dla użytkownika, który jest uruchomiony kod. Ta operacja <xref:System.Security.Permissions.IsolatedStorageFilePermission> wymaga <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> uprawnień dla wartości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje użycie metod statycznych i wystąpienia. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> Klasa uzyskuje dwa magazyny; jeden jest izolowany dla użytkownika i zestawu, a drugi jest izolowany dla użytkownika, domeny i zestawu. Użytkownik, domena i magazyn zestawów są <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> następnie usuwane przez `isoStore1`wywołanie metody izolowanego pliku magazynu . Następnie wszystkie pozostałe magazyny dla użytkownika są <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>usuwane przez wywołanie metody statycznej .  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
