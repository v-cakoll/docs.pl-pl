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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708118"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Porady: przewidywanie warunków braku miejsca w izolowanym magazynie

Kod korzystający z izolowanego magazynu jest ograniczony przez [przydział](../../../docs/standard/io/isolated-storage.md#quotas) , który określa maksymalny rozmiar przedziału danych, w którym znajdują się pliki i katalogi izolowanych magazynów. Przydział jest definiowany przez zasady zabezpieczeń i jest konfigurowalny przez administratorów. Jeśli maksymalny dozwolony rozmiar zostanie przekroczony podczas próby zapisu danych, zostanie zgłoszony wyjątek <xref:System.IO.IsolatedStorage.IsolatedStorageException> i operacja nie powiedzie się. Pomaga to zapobiegać złośliwym atakom typu "odmowa usługi", co może spowodować odrzucenie żądań przez aplikację, ponieważ magazyn danych jest wypełniony.

Aby ułatwić określenie, czy dana próba zapisu prawdopodobnie nie powiedzie się z tego powodu, Klasa <xref:System.IO.IsolatedStorage.IsolatedStorage> udostępnia trzy właściwości tylko do odczytu: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Za pomocą tych właściwości można określić, czy zapis w sklepie spowoduje przekroczenie maksymalnego dozwolonego rozmiaru magazynu. Należy pamiętać, że dostęp do wydzielonego magazynu jest możliwy współbieżnie; w związku z tym podczas obliczania ilości pozostałego miejsca do magazynowania mogą być używane przez czas, w którym próbujesz zapisać w sklepie. Można jednak użyć maksymalnego rozmiaru magazynu, aby określić, czy górny limit dostępnego magazynu ma zostać osiągnięty.

Właściwość <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> zależy od dowodów z zestawu, aby działała prawidłowo. Z tego powodu należy pobrać tę właściwość tylko na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które zostały utworzone przy użyciu metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiekty, które zostały utworzone w inny sposób (na przykład obiekty, które zostały zwrócone z metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>) nie będą zwracać dokładnego maksymalnego rozmiaru.

## <a name="example"></a>Przykład

Poniższy przykład kodu uzyskuje izolowany magazyn, tworzy kilka plików i pobiera właściwość <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>. Pozostałe miejsce jest raportowane w bajtach.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
- [Instrukcje: uzyskiwanie magazynów dla wydzielonej pamięci masowej](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
