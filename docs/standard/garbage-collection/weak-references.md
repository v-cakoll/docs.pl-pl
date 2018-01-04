---
title: "Słabe odwołania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ca1331cc45f437882d38adba241e2767821de36
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="weak-references"></a>Słabe odwołania
Moduł zbierający elementy bezużyteczne nie można zebrać obiektu używany przez aplikację, gdy kod aplikacji może osiągnąć tego obiektu. Aplikacja jest nazywany ma silne odwołanie do obiektu.  
  
 Słabe odwołanie zezwala na moduł garbage collector zbierać obiektu, umożliwiając aplikacji dostępu do tego obiektu. Słabe odwołanie jest prawidłowy tylko w nieokreślonej ilość czasu, aż obiekt są gromadzone, gdy nie występują żadne relacje silne. Gdy używasz słabe odwołanie silne odwołanie do obiektu, który uniemożliwia zbieranych nadal można korzystać z aplikacji. Jednak zawsze istnieje ryzyko, że moduł zbierający elementy bezużyteczne rozpocznie się obiekt najpierw przed ustanowieniu silne odwołanie.  
  
 Słabe odwołania są przydatne w przypadku obiektów, które używają dużej ilości pamięci, ale można utworzyć ponownie łatwo Jeśli odzyskane przez wyrzucanie elementów bezużytecznych.  
  
 Załóżmy, że widok drzewa w aplikacji formularzy systemu Windows wyświetla złożonych hierarchiczna wybór opcji dla użytkownika. W przypadku dużych danych utrzymywanie drzewa w pamięci jest nieefektywne, gdy użytkownik jest związany z innych obiektów w aplikacji.  
  
 Gdy użytkownik zmienia optymalizacji na inną część aplikacji, można użyć <xref:System.WeakReference> klasa do tworzenia słabe odwołanie do drzewa i zniszczyć wszystkie odwołania silne. Gdy użytkownik przełącza do drzewa, aplikacja próbuje uzyskać silne odwołanie do drzewa i w razie powodzenia pozwala uniknąć Rekonstruowanie drzewa.  
  
 Aby ustanowić słabe odwołanie z obiektem, należy utworzyć <xref:System.WeakReference> mają być śledzone za pomocą wystąpienia obiektu. Następnie ustaw <xref:System.WeakReference.Target%2A> właściwości tego obiektu i zestawu oryginalnej odwołanie do obiektu `null`. Na przykład kod, zobacz <xref:System.WeakReference> w bibliotece klas.  
  
## <a name="short-and-long-weak-references"></a>Krótko- i długi słabe odwołania  
 Można utworzyć krótkiej słabe odwołanie lub długo słabego odwołania:  
  
-   krótki  
  
     Element docelowy krótkich słabe odwołanie staje się `null` gdy obiekt jest odzyskana przez wyrzucanie elementów bezużytecznych. Słabe odwołanie jest obiekt zarządzany i mogą ulec wyrzucanie elementów bezużytecznych, podobnie jak inne obiektu zarządzanego.  Krótki słabe odwołanie jest domyślnego konstruktora dla <xref:System.WeakReference>.  
  
-   długa  
  
     Long słabe odwołanie jest zachowywane po obiektu <xref:System.Object.Finalize%2A> została wywołana metoda. Dzięki temu obiekt do odtworzenia, ale stan obiektu pozostaje nieprzewidywalne. Aby korzystać z odwołaniem długie, określ `true` w <xref:System.WeakReference> konstruktora.  
  
     Jeśli typ obiektu nie ma <xref:System.Object.Finalize%2A> stosuje funkcji krótkich słabe odwołanie metody, a słabe odwołanie jest prawidłowe tylko do momentu docelowej są zbierane, co może nastąpić w dowolnym momencie po finalizatora jest uruchomienie.  
  
 Aby ustanowić silne odwołanie i ponownie użyć obiektu, rzutowania <xref:System.WeakReference.Target%2A> właściwość <xref:System.WeakReference> do typu obiektu. Jeśli <xref:System.WeakReference.Target%2A> zwraca `null`, obiekt był zebranych; w przeciwnym razie, można nadal używać obiektu, ponieważ aplikacja została ponownie nawiązana silne odwołanie do niej.  
  
## <a name="guidelines-for-using-weak-references"></a>Wskazówki dotyczące używania słabe odwołania  
 Użyj długo słabe odwołania tylko wtedy, gdy jest to konieczne, ponieważ stan obiektu jest nieprzewidziany po zakończeniu.  
  
 Unikaj używania słabego odwołania do obiektów małych wskaźnik sam może być tak dużych lub większy.  
  
 Unikaj używania słabe odwołania jako automatyczne rozwiązanie problemów z zarządzaniem pamięci. Zamiast tego Tworzenie skutecznych zasad buforowania obsługi obiektów aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
