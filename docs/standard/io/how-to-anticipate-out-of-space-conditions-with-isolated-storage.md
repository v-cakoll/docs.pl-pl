---
title: 'Instrukcje: Przewidywanie warunków limit miejsca w wydzielonej pamięci masowej'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf5144cb1abd3a916d2b5afc361c8c96a221d47e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372298"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Instrukcje: Przewidywanie warunków limit miejsca w wydzielonej pamięci masowej

Kod, który używa wydzielona pamięć masowa jest ograniczony przez [przydziału](../../../docs/standard/io/isolated-storage.md#quotas) , który określa maksymalny rozmiar przedział danych, w którym izolowany magazyn plików i katalogów istnieje. Limit przydziału jest definiowany przez zasady zabezpieczeń i jest konfigurowane przez administratorów. Gdy maksymalny dozwolony rozmiar zostanie przekroczony podczas próby zapisu danych, <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku i kończy się niepowodzeniem. Pozwala to zapobiec złośliwymi atakami typu "odmowa usługi", które może spowodować, że aplikacja odmowy żądania, ponieważ Magazyn danych jest wypełnione.

Aby ułatwić ustalenie, czy próba zapisu danego prawdopodobnie się nie powieść z tego powodu <xref:System.IO.IsolatedStorage.IsolatedStorage> klasa udostępnia trzy właściwości tylko do odczytu: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Te właściwości można użyć do określenia, czy zapisywanie w magazynie spowoduje, że maksymalny dozwolony rozmiar magazynu zostać przekroczony. Należy pamiętać, że isolated storage może być uzyskiwany współbieżnie, w związku z tym gdy obliczeniowe ilości pozostałego magazynu miejsca do magazynowania może być używana przez czas podczas próby zapisu w magazynie. Jednak można użyć maksymalny rozmiar magazynu w celu określenia, czy górny limit na dostępny magazyn jest wkrótce osiągnięty.

<xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Właściwości zależy od dowodów z zestawu, aby zapewnić prawidłowe działanie. Z tego powodu należy pobrać tej właściwości, tylko na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które zostały utworzone przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiekty, które zostały utworzone w jakikolwiek inny sposób (na przykład, obiekty, które zostały zwrócone przez <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda) nie będzie zwracać odpowiedni rozmiar maksymalny.

## <a name="example"></a>Przykład

Poniższy przykładowy kod uzyskuje w izolowanym magazynie, tworzy kilka plików i pobiera <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> właściwości. Ilość wolnego miejsca jest zgłaszany w bajtach.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
- [Instrukcje: Uzyskiwanie magazynów dla wydzielonej pamięci masowej](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
