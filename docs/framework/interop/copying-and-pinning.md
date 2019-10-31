---
title: Kopiowanie i przypinanie
ms.date: 03/30/2017
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
ms.openlocfilehash: f6db7d37293015911c1285d39e19bf7542a7ac59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123639"
---
# <a name="copying-and-pinning"></a>Kopiowanie i przypinanie

Podczas organizowania danych Organizator międzyoperacyjny może skopiować lub przypiąć dane, które są organizowane. Kopiowanie danych powoduje umieszczenie kopii danych z jednej lokalizacji w innej lokalizacji pamięci. Na poniższej ilustracji przedstawiono różnice między kopiowaniem typu wartości i kopiowaniem typu przekazana przez odwołanie z zarządzanej do niezarządzanej pamięci.

![Diagram przedstawiający sposób kopiowania typów wartości i odwołań.](./media/copying-and-pinning/interop-marshal-copy.gif)

Argumenty metody przekazywane przez wartość są organizowane w kodzie niezarządzanym jako wartości na stosie. Proces kopiowania jest bezpośredni. Argumenty przekazane przez odwołanie są przekazane jako wskaźniki na stosie. Typy odwołań są również przesyłane przez wartość i przez odwołanie. Jak widać na poniższej ilustracji, typy odwołań przekazana przez wartość są kopiowane lub przypinane:

![Diagram przedstawiający typy odwołań, które są przesyłane przez wartość i przez odwołanie.](./media/copying-and-pinning/interop-marshal-reference-pin.gif)

Przypinanie tymczasowo powoduje tymczasowe zablokowanie danych w bieżącej lokalizacji pamięci, dzięki czemu nie należy ich przełączać przez moduł wyrzucania elementów bezużytecznych środowiska uruchomieniowego języka wspólnego. Organizator przypina dane, aby zmniejszyć koszty kopiowania i zwiększania wydajności. Typ danych określa, czy jest on kopiowany, czy przypięty podczas procesu organizowania.  Przypinanie jest wykonywane automatycznie podczas organizowania obiektów, takich jak <xref:System.String>, jednak można również ręcznie przypiąć pamięć przy użyciu klasy <xref:System.Runtime.InteropServices.GCHandle>.

## <a name="formatted-blittable-classes"></a>Sformatowane klasy danych kopiowalnych

Sformatowane klasy [danych kopiowalnych](blittable-and-non-blittable-types.md) mają stały układ (sformatowany) i wspólne reprezentację danych w pamięci zarządzanej i niezarządzanej. Gdy te typy wymagają kierowania, wskaźnik do obiektu w stercie jest przekazywany do elementu wywoływanego bezpośrednio. Wywoływany może zmienić zawartość lokalizacji pamięci, do której odwołuje się wskaźnik.

> [!NOTE]
> Wywoływany może zmienić zawartość pamięci, jeśli parametr jest oznaczony jako out lub out. Z drugiej strony, obiekt wywoływany powinien unikać zmiany zawartości, gdy parametr jest ustawiony na wartość Marshal jako w, która jest wartością domyślną dla sformatowanych typów danych kopiowalnych. Modyfikowanie obiektu w programie generuje problemy, gdy ta sama klasa jest eksportowana do biblioteki typów i używana do wykonywania wywołań między komórkami.

## <a name="formatted-non-blittable-classes"></a>Sformatowane klasy inne niż danych kopiowalnych

Sformatowane klasy [inne niż danych kopiowalnych](blittable-and-non-blittable-types.md) mają stały układ (sformatowany), ale reprezentacja danych różni się w pamięci zarządzanej i niezarządzanej. Dane mogą wymagać przekształcenia w następujących warunkach:

- Jeśli Klasa inny niż danych kopiowalnych jest zorganizowany przez wartość, wywoływany otrzymuje wskaźnik do kopii struktury danych.

- Jeśli Klasa niedanych kopiowalnycha jest organizowana przez odwołanie, wywoływany otrzymuje wskaźnik do wskaźnika do kopii struktury danych.

- Jeśli atrybut <xref:System.Runtime.InteropServices.InAttribute> jest ustawiony, ta kopia jest zawsze inicjowana przy użyciu stanu wystąpienia, kierując w razie potrzeby.

- Jeśli atrybut <xref:System.Runtime.InteropServices.OutAttribute> jest ustawiony, stan jest zawsze kopiowany z powrotem do wystąpienia w przypadku powrotu, organizowania w razie potrzeby.

- Jeśli ustawiono zarówno **atrybut unattribute** , jak i **atrybut** , wymagane są obie kopie. Jeśli jeden atrybut zostanie pominięty, organizator może zoptymalizować, eliminując każdą kopię.

## <a name="reference-types"></a>Typy odwołań

Typy odwołań mogą być przesyłane przez wartość lub przez odwołanie. Gdy są one przesyłane przez wartość, wskaźnik do typu jest przesyłany na stosie. Po przekazaniu przez odwołanie wskaźnik do wskaźnika do typu jest przenoszona na stosie.

Typy odwołań mają następujące zachowanie warunkowe:

- Jeśli typ referencyjny jest przesyłany przez wartość i ma elementy członkowskie typu innego niż danych kopiowalnych, typy są konwertowane dwa razy:

  - Gdy argument jest przenoszona do niezarządzanej strony.

  - Przy powrocie z wywołania.

  Aby uniknąć niepotrzebnego kopiowania i konwersji, te typy są organizowane jako parametry. Należy jawnie zastosować atrybuty **InAttribute** i **Attribute** do argumentu obiektu wywołującego, aby zobaczyć zmiany wprowadzone przez wywoływany element.

- Jeśli typ odwołania jest przekazywany przez wartość i ma tylko elementy członkowskie typów danych kopiowalnych, może być przypięty podczas organizowania, a wszelkie zmiany wprowadzone do elementów członkowskich typu przez obiekt wywoływany są widoczne przez wywołującego. W przypadku tego zachowania należy jawnie zastosować **atrybut Attribute** i **subattribute** . Bez tych atrybutów kierunkowych Organizator międzyoperacyjny nie eksportuje informacji kierunkowych do biblioteki typów (eksportuje ją jako wartość domyślna) i może to spowodować problemy z kierowaniem między projektami COM.

- Jeśli typ odwołania jest przekazywany przez odwołanie, będzie on domyślnie zorganizowany jako przewidziany jako element.

## <a name="systemstring-and-systemtextstringbuilder"></a>System. String i system. Text. StringBuilder

Gdy dane są przekazywane do kodu niezarządzanego przez wartość lub przez odwołanie, organizator zazwyczaj kopiuje dane do pomocniczego bufora (może to być spowodowane konwersją zestawów znaków podczas kopiowania) i przekazuje odwołanie do buforu do elementu wywoływanego. O ile odwołanie nie jest znakiem **BSTR** przydzielonym **SysAllocString**, odwołanie jest zawsze przyliczane z **CoTaskMemAlloc**.

Jako Optymalizacja, gdy jeden typ ciągu jest zorganizowany przez wartość (na przykład ciąg znaków Unicode), organizator przekazuje wywoływany bezpośredni wskaźnik do zarządzanych ciągów w wewnętrznym buforze Unicode zamiast kopiować go do nowego buforu.

> [!CAUTION]
> Gdy ciąg jest przekazywany przez wartość, wywoływany element nie może zmieniać odwołania przekazywanego przez organizatora. Wykonanie tej operacji może spowodować uszkodzenie sterty zarządzanej.

Gdy <xref:System.String?displayProperty=nameWithType> jest przekazywany przez odwołanie, organizator kopiuje zawartość ciągu do pomocniczego buforu przed wywołaniem. Następnie zawartość bufora jest kopiowana do nowego ciągu przy powrocie z wywołania. Ta technika zapewnia, że niezmienny ciąg zarządzany pozostanie niezmieniony.

Gdy <xref:System.Text.StringBuilder?displayProperty=nameWithType> jest przekazywany przez wartość, organizator przekazuje odwołanie do wewnętrznego buforu **StringBuilder** bezpośrednio do obiektu wywołującego. Obiekt wywołujący i wywoływany muszą zgadzać się z rozmiarem buforu. Obiekt wywołujący jest odpowiedzialny za utworzenie elementu **StringBuilder** o odpowiedniej długości. Obiekt wywoływany musi wykonać odpowiednie środki ostrożności, aby upewnić się, że bufor nie zostanie przepełniony. **StringBuilder** jest wyjątkiem od reguły, której typy odwołań przesłane przez wartość są domyślnie przesyłane jako parametry w parametrach. Jest on zawsze przenoszona jako wynikowy.

## <a name="see-also"></a>Zobacz także

- [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)
- [Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Marshaling międzyoperacyjny](interop-marshaling.md)
