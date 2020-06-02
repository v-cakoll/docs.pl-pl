---
title: 'Instrukcje: Przewidywanie warunków braku miejsca w izolowanym magazynie'
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
ms.openlocfilehash: bdc2cee343e9d9be44230e84ff45d6fa54901f48
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288592"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Instrukcje: Przewidywanie warunków braku miejsca w izolowanym magazynie

Kod korzystający z izolowanego magazynu jest ograniczony przez [przydział](isolated-storage.md#quotas) , który określa maksymalny rozmiar przedziału danych, w którym znajdują się pliki i katalogi izolowanych magazynów. Przydział jest definiowany przez zasady zabezpieczeń i jest konfigurowalny przez administratorów. Jeśli maksymalny dozwolony rozmiar zostanie przekroczony podczas próby zapisu danych, <xref:System.IO.IsolatedStorage.IsolatedStorageException> zgłaszany jest wyjątek, a operacja kończy się niepowodzeniem. Pomaga to zapobiegać złośliwym atakom typu "odmowa usługi", co może spowodować odrzucenie żądań przez aplikację, ponieważ magazyn danych jest wypełniony.

Aby ułatwić określenie, czy dana próba zapisu prawdopodobnie nie powiedzie się z tego powodu, <xref:System.IO.IsolatedStorage.IsolatedStorage> Klasa zawiera trzy właściwości tylko do odczytu: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> , <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> , i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> . Za pomocą tych właściwości można określić, czy zapis w sklepie spowoduje przekroczenie maksymalnego dozwolonego rozmiaru magazynu. Należy pamiętać, że dostęp do wydzielonego magazynu jest możliwy współbieżnie; w związku z tym podczas obliczania ilości pozostałego miejsca do magazynowania mogą być używane przez czas, w którym próbujesz zapisać w sklepie. Można jednak użyć maksymalnego rozmiaru magazynu, aby określić, czy górny limit dostępnego magazynu ma zostać osiągnięty.

<xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>Właściwość zależy od dowodów z zestawu, aby działała prawidłowo. Z tego powodu należy pobrać tę właściwość tylko dla <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które zostały utworzone przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> metody, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> . <xref:System.IO.IsolatedStorage.IsolatedStorageFile>obiekty, które zostały utworzone w inny sposób (na przykład obiekty, które zostały zwrócone z <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody) nie będą zwracać dokładnego maksymalnego rozmiaru.

## <a name="example"></a>Przykład

Poniższy przykład kodu uzyskuje izolowany magazyn, tworzy kilka plików i pobiera <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> Właściwość. Pozostałe miejsce jest raportowane w bajtach.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Magazyn izolowany](isolated-storage.md)
- [Instrukcje: Uzyskiwanie magazynów dla izolowanego magazynu](how-to-obtain-stores-for-isolated-storage.md)
