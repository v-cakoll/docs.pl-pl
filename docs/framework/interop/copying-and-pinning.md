---
title: Kopiowanie i przypinanie
ms.date: 03/30/2017
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42257790b5a6e5005ca142bd5e32d4c6fc545195
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507086"
---
# <a name="copying-and-pinning"></a>Kopiowanie i przypinanie
Podczas przekazywania danych, organizator międzyoperacyjny można skopiować lub przypiąć dane są przekazywane. Kopiowanie danych umieszcza kopię danych z jednej lokalizacji pamięci w innej lokalizacji w pamięci. Na poniższej ilustracji przedstawiono różnice między kopiowanie typu wartości i kopiowanie typu przekazywane przez odwołanie z kodu zarządzanego do niezarządzanej pamięci.  
  
 ![Typy przekazywane według wartości i według odwołania wartości](./media/interopmarshalcopy.gif "interopmarshalcopy")  
Typy wartości przekazywane według wartości i według odwołania  
  
 Przekazywane przez wartość argumenty metody są przekazywania do kodu niezarządzanego jako wartości na stosie. Proces kopiowania jest bezpośrednie. Argumenty przekazywane przez odwołanie, są przekazywane jako wskaźniki na stosie. Typy odwołań również są przekazywane według wartości i według odwołania. Jak pokazano na poniższej ilustracji, typy odwołań, przekazać przez wartość są kopiowane lub przypięty.  
  
 ![Usługa międzyoperacyjna modelu COM](./media/interopmarshalpin.gif "interopmarshalpin")  
Typy odwołań przekazywane według wartości i według odwołania  
  
 Przypinanie tymczasowo blokuje danych w jego bieżącej lokalizacji pamięci, dlatego zachowywanie ich z są przemieszczane przez moduł zbierający elementy bezużyteczne wykonywalnych języka wspólnego. Organizator Przypina dane, aby zmniejszyć obciążenie kopiowania i zwiększyć wydajność. Typ danych określa, czy jest kopiowany lub przypiąć podczas organizowania procesu.  Przypinanie jest wykonywane automatycznie podczas marshaling dla obiektów, takich jak <xref:System.String>, ale można też ręcznie przypiąć przy użyciu pamięci <xref:System.Runtime.InteropServices.GCHandle> klasy.  
  
## <a name="formatted-blittable-classes"></a>Klasy sformatowanych danych Kopiowalnych  
 Sformatowana [danych kopiowalnych](blittable-and-non-blittable-types.md) klasy naprawiona układu (sformatowany) i wspólne reprezentacji danych w obu zarządzanych i niezarządzanych pamięci. Te typy potrzebują, organizowanie, wskaźnik do obiektu w stosie jest przekazywany do obiekt wywoływany bezpośrednio. Obiekt wywoływany może zmienić zawartość lokalizacji pamięci, do którego nastąpiło odwołanie przez wskaźnik.  
  
> [!NOTE]
>  Obiekt wywoływany można zmienić zawartość pamięci, jeśli parametr jest oznaczony jako, Out ani wchodzącym/wychodzącym. Z kolei obiekt wywoływany należy unikać zmiany zawartości, gdy ustawiona jest przeprowadzanie marshalingu obiektu, na przykład co jest ustawieniem domyślnym dla typów danych kopiowalnych sformatowany. Modyfikowanie obiektu w generuje problemy podczas eksportowania tej samej klasy do biblioteki typów i używane do nawiązywania połączeń typu apartment krzyżowe.  
  
## <a name="formatted-non-blittable-classes"></a>Klasy sformatowane Niekopiowalnych  
 Sformatowana [niekopiowalnych](blittable-and-non-blittable-types.md) klasy naprawiona układu (sformatowany), ale reprezentacji danych różni się w pamięci zarządzanych i niezarządzanych. Dane mogą wymagać przekształcenia w następujących warunkach:  
  
-   Jeśli klasa niekopiowalnych jest przekazywany przez wartość, obiekt wywoływany otrzymuje wskaźnik kopię struktury danych.  
  
-   Jeśli klasa niekopiowalnych jest przekazywany przez odwołanie, obiekt wywoływany otrzymuje wskaźnik do wskaźnika na kopię struktury danych.  
  
-   Jeśli <xref:System.Runtime.InteropServices.InAttribute> ma ustawioną wartość atrybutu, tej kopii zawsze jest inicjowany ze stanem wystąpienia, organizowanie zgodnie z potrzebami.  
  
-   Jeśli <xref:System.Runtime.InteropServices.OutAttribute> ma ustawioną wartość atrybutu, stan jest zawsze kopiowane z powrotem do wystąpienia na zwracania, przekazywania międzyprocesowego zgodnie z potrzebami.  
  
-   Jeśli oba **InAttribute** i **OutAttribute** są ustawione, obydwie kopie są wymagane. W przypadku pominięcia albo atrybut Organizator można zoptymalizować poprzez wyeliminowanie skopiuj.  
  
## <a name="reference-types"></a>Typy odwołań  
 Typy odwołań może być przekazywany przez wartość lub przez odwołanie. Gdy są przekazywane według wartości, wskaźnikiem do typu jest przekazywane na stosie. Gdy dane są przekazywane przez odwołanie, wskaźnik do wskaźnika do typu jest przekazywane na stosie.  
  
 Typy odwołań mają następujące zachowanie warunkowego:  
  
-   Jeśli typ odwołania jest przekazywany przez wartość i ma składowe typów niekopiowalnych, typy są konwertowane dwa razy:  
  
    -   Gdy argument jest przekazywany do niezarządzanym.  
  
    -   Na powrót z wywołania.  
  
     Aby uniknąć niepotrzebnego kopiowania i konwersji, te typy są organizowane podobnie jak w parametrach. Należy wyraźnie zastosujesz **InAttribute** i **OutAttribute** atrybuty do argumentu do obiektu wywołującego zobaczyć zmiany wprowadzone przez obiekt wywoływany.  
  
-   Jeśli typ odwołania jest przekazywany przez wartość i ma tylko członkowie kopiowalnymi, mogą być przypinane podczas przekazywania międzyprocesowego i wszelkie zmiany wprowadzone przez obiekt wywoływany elementy członkowskie tego typu są widoczne przez obiekt wywołujący. Zastosuj **InAttribute** i **OutAttribute** jawnie, jeśli chcesz, aby to zachowanie. Bez tych atrybutów kierunkowe, organizator międzyoperacyjny nie eksportuje kierunkowe informacji do biblioteki typów (Eksportuje ona na przykład jest to ustawienie domyślne) i może to spowodować problemy z szeregowanie między apartamentu COM.  
  
-   Jeśli typ odwołania jest przekazywany przez odwołanie, jej będzie można zorganizować jako we/wy domyślnie.  
  
## <a name="systemstring-and-systemtextstringbuilder"></a>System.String i elementu System.Text.StringBuilder  
 Gdy data jest przekazywania do kodu niezarządzanego przez wartość lub przez odwołanie, organizator zazwyczaj kopiuje dane do dodatkowej buforu (konwertowanie prawdopodobnie zestawów znaków podczas kopiowania) i przekazuje odwołania do buforu obiekt wywoływany. O ile nie jest odwołanie **BSTR** przydzielonymi **SysAllocString**, odwołanie jest zawsze przydzielana za pomocą **CoTaskMemAlloc**.  
  
 Optymalizacji podczas dowolnego typu ciąg jest przekazywany przez wartość (na przykład ciąg znaków Unicode) Organizator przekazuje obiekt wywoływany bezpośredni wskaźnik do zarządzane ciągi do wewnętrznego buforu Unicode, zamiast go przepisywać, aby bufor nowego.  
  
> [!CAUTION]
>  Jeśli ciąg jest przekazywany przez wartość, obiekt wywoływany nigdy nie może zmieniać odwołania przekazywane przez organizatora. Ten sposób może uszkodzić zarządzanego stosu.  
  
 Gdy <xref:System.String?displayProperty=nameWithType> jest przekazywany przez odwołanie, organizator kopiuje zawartość ciągu do buforu pomocniczej przed wykonaniem wywołania. Następnie kopiuje zawartość buforu do nowego ciągu na powrót z wywołania. Ta technika gwarantuje, że niezmienny ciąg zarządzanych pozostaje niezmienione.  
  
 Gdy <xref:System.Text.StringBuilder?displayProperty=nameWithType> jest przekazywany przez wartość i przekazuje organizatora, a odwołanie do wewnętrznego buforu elementu **StringBuilder** bezpośrednio do obiektu wywołującego. Obiektami wywołującym i wywoływanym należy uzgodnić rozmiar buforu. Obiekt wywołujący jest odpowiedzialny za tworzenie **StringBuilder** odpowiednią długość. Obiekt wywoływany musi podjąć niezbędne środki ostrożności, aby upewnić się, że nie przepełnienie buforu. **StringBuilder** są wyjątkiem od reguły, który przekazywane według wartości typy odwołań są przekazywane w parametrach domyślnie. Jest zawsze przekazywana jako we/wy.  
  
## <a name="see-also"></a>Zobacz także
- [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)
- [Zarządzanie pamięcią za pomocą organizatora międzyoperacyjnego](https://msdn.microsoft.com/library/417206ce-ee3e-4619-9529-0c0b686c7bee(v=vs.100))
- [Atrybuty kierunkowe](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))
- [Marshaling międzyoperacyjny](interop-marshaling.md)
