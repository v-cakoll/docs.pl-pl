---
title: 'Instrukcje: Usuwanie danych z izolowanego magazynu'
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
ms.openlocfilehash: 885dc8e3ca0ea99de460cee7dd093b061f916388
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291893"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Instrukcje: Usuwanie danych z izolowanego magazynu
<xref:System.IO.IsolatedStorage.IsolatedStorageFile>Klasa udostępnia dwie metody usuwania izolowanych plików magazynu:  
  
- Metoda instance nie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> przyjmuje żadnych argumentów i usuwa magazyn, który go wywołuje. Dla tej operacji nie są wymagane żadne uprawnienia. Każdy kod, który może uzyskać dostęp do sklepu, może usunąć wszystkie lub wszystkie znajdujące się w nim dane.  
  
- Metoda statyczna <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartość wyliczenia i usuwa wszystkie magazyny dla użytkownika, który uruchomił kod. Ta operacja wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnienia do <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie metod statycznych i wystąpień <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> . Klasa uzyskuje dwa magazyny; jeden jest izolowany dla użytkownika i zestawu, a drugi jest izolowany dla użytkownika, domeny i zestawu. Użytkownik, domena i magazyn zestawów są następnie usuwane przez wywołanie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metody pliku magazynu izolowanego `isoStore1` . Następnie wszystkie pozostałe magazyny dla użytkownika są usuwane przez wywołanie metody statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> .  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Magazyn izolowany](isolated-storage.md)
