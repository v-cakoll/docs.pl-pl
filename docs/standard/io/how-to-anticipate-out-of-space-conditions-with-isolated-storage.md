---
title: 'Porady: przewidywanie warunków braku miejsca w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
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
ms.openlocfilehash: 5666019e1a65880221261ef5ad704f82c37263b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708118"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Porady: przewidywanie warunków braku miejsca w izolowanym magazynie

Kod, który używa izolowanego magazynu jest ograniczony przez [przydział,](../../../docs/standard/io/isolated-storage.md#quotas) który określa maksymalny rozmiar przedziału danych, w którym istnieją izolowane pliki magazynu i katalogi. Przydział jest definiowany przez zasady zabezpieczeń i jest konfigurowalny przez administratorów. Jeśli maksymalny dozwolony rozmiar zostanie przekroczony podczas <xref:System.IO.IsolatedStorage.IsolatedStorageException> próby zapisania danych, wyjątek zostanie zgłoszony, a operacja zakończy się niepowodzeniem. Pomaga to zapobiegać złośliwym atakom typu "odmowa usługi", które mogą spowodować, że aplikacja odrzuci żądania, ponieważ magazyn danych jest wypełniony.

Aby ułatwić określenie, czy dana próba zapisu może <xref:System.IO.IsolatedStorage.IsolatedStorage> zakończyć się niepowodzeniem z <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>tego <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>powodu, klasa zawiera trzy właściwości tylko do odczytu: , , i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Można użyć tych właściwości, aby ustalić, czy zapis do magazynu spowoduje maksymalny dozwolony rozmiar magazynu, które mają zostać przekroczone. Należy pamiętać, że izolowany magazyn jest dostępny jednocześnie; w związku z tym podczas obliczania ilości pozostałego magazynu, miejsce do magazynowania może być zużyte przez czas próby zapisu do magazynu. Można jednak użyć maksymalnego rozmiaru magazynu, aby określić, czy górny limit dostępnego magazynu ma zostać osiągnięty.

Właściwość <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> zależy od dowodów z zestawu do prawidłowego działania. Z tego powodu należy pobrać tę <xref:System.IO.IsolatedStorage.IsolatedStorageFile> właściwość tylko na obiekty, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>które <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> zostały utworzone przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, , lub metody. <xref:System.IO.IsolatedStorage.IsolatedStorageFile>obiekty, które zostały utworzone w jakikolwiek inny sposób (na <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> przykład obiekty, które zostały zwrócone z metody) nie zwróci dokładny maksymalny rozmiar.

## <a name="example"></a>Przykład

Poniższy przykład kodu uzyskuje izolowany magazyn, tworzy kilka <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> plików i pobiera właściwość. Pozostałe miejsce jest zgłaszane w bajtach.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
- [Porady: uzyskiwanie magazynów dla izolowanego magazynu](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
