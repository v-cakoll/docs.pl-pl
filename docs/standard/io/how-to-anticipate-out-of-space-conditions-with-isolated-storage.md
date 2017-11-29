---
title: "Porady: przewidywanie warunków braku miejsca w izolowanym magazynie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d813522d0aeb9bf37582c167760d44268df27039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Porady: przewidywanie warunków braku miejsca w izolowanym magazynie
Kod, który korzysta z magazynu izolowanego jest ograniczane przez [przydziału](../../../docs/standard/io/isolated-storage.md#quotas) , który określa maksymalny rozmiar dla przedziału danych, w którym odizolowane pliki i katalogi istnieją. Limit przydziału jest definiowana za pomocą zasad zabezpieczeń i jest konfigurowane przez administratorów. Jeśli maksymalny dozwolony rozmiar jest przekroczony podczas próby zapisu danych, <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku i kończy się niepowodzeniem. Pomaga to zapobiec złośliwymi atakami typu "odmowa usługi", które może spowodować aplikacji odrzucać żądania, ponieważ Magazyn danych jest wypełnione.  
  
 Aby ułatwić określenie, czy mogą kończyć się niepowodzeniem z tego powodu, próba zapisu danego <xref:System.IO.IsolatedStorage.IsolatedStorage> klasa udostępnia trzy właściwości tylko do odczytu: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Te właściwości można użyć do określenia, czy zapisywanie w magazynie spowoduje, że maksymalny dozwolony rozmiar magazynu przekroczenie. Należy pamiętać, że izolowanego magazynu jest możliwy jednocześnie; w związku z tym obliczeniowe ilości pozostałego miejsca, miejsca do magazynowania może być używane podczas próby zapisu w magazynie. Jednak służy maksymalny rozmiar magazynu w celu określenia, czy górny limit na dostępny magazyn o się można nawiązać połączenia.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Właściwość zależy od dowód z zestawu do poprawnego działania. Z tego powodu tej właściwości powinno pobrać tylko na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które zostały utworzone przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. <xref:System.IO.IsolatedStorage.IsolatedStorageFile>obiekty, które zostały utworzone w inny sposób (na przykład w przypadku obiektów, które zostały zwrócone z <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda) nie zwróci odpowiedni rozmiar maksymalny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod uzyskuje izolowanego magazynu tworzy kilka plików i pobiera <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> właściwości. Pozostałe miejsce jest zgłaszana w bajtach.  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Izolowany Magazyn](../../../docs/standard/io/isolated-storage.md)  
 [Porady: uzyskiwanie magazynów dla izolowanego magazynu](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
