---
title: Organizowanie różnych typów tablic
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: 66c7ba5989952edb55f21aab960ad7395a92ae0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181365"
---
# <a name="marshaling-different-types-of-arrays"></a>Organizowanie różnych typów tablic
Tablica jest typem odwołania w kodzie zarządzanym, który zawiera jeden lub więcej elementów tego samego typu. Chociaż tablice są typami odwołań, są one przekazywane jako w parametrach do funkcji niezarządzanych. To zachowanie jest niezgodne ze sposobem, w jaki tablice zarządzane są przekazywane do obiektów zarządzanych, co jest parametrami W/Wyjście. Aby uzyskać dodatkowe informacje, zobacz [Kopiowanie i przypinanie](copying-and-pinning.md).  
  
 W poniższej tabeli wymieniono opcje organizowania tablic i opisano ich użycie.  
  
|Tablica|Opis|  
|-----------|-----------------|  
|Liczba całkowita według wartości.|Przekazuje tablicę liczby całkowitej jako parametr In.|  
|Liczba całkowita przez odwołanie.|Przekazuje tablicę liczby całkowitej jako parametr In/Out.|  
|Liczba całkowita według wartości (dwuwymiarowa).|Przekazuje macierz liczby całkowite jako parametr In.|  
|Ciągów według wartości.|Przekazuje tablicę ciągów jako parametr In.|  
|Struktur z liczbami całkowitymi.|Przekazuje tablicę struktur, które zawierają liczby całkowite jako In parametru.|  
|Ze struktur ze sznurkami.|Przekazuje tablicę struktur, które zawierają tylko ciągi jako parametr In/Out. Elementy członkowskie tablicy można zmienić.|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak przekazać następujące typy tablic:  
  
- Tablica liczby całkowitych według wartości.  
  
- Tablica liczby całkowitych przez odwołanie, które mogą być przesiąknięte.  
  
- Tablica wielowymiarowa (macierz) liczby całkowite według wartości.  
  
- Tablica ciągów według wartości.  
  
- Tablica struktur z liczbami całkowitymi.  
  
- Tablica struktur z ciągami.  
  
 Chyba że tablica jest jawnie organizowane przez odwołanie, domyślne zachowanie marszałków tablicy jako In parametru. To zachowanie można zmienić, <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> stosując jawnie atrybuty i.  
  
 Arrays przykład używa następujących funkcji niezarządzanych, pokazane z ich oryginalnej deklaracji funkcji:  
  
- **TestArrayOfInts** eksportowane z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- **TestRefArrayOfInts** eksportowane z PinvokeLib.dll.  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- **TestMatrixOfInts** eksportowane z PinvokeLib.dll.  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- **TestArrayOfStrings** eksportowane z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- **TestArrayOfStructs** eksportowane z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- **TestArrayOfStructs2** eksportowane z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa biblioteka niezarządzana, która zawiera implementacje dla wcześniej wymienionych funkcji i dwie zmienne struktury, **MYPOINT** i **MYPERSON**. Struktury zawierają następujące elementy:  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 W tym `MyPoint` przykładzie `MyPerson` i struktur zawierają typy osadzone. Atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> jest ustawiony, aby upewnić się, że elementy członkowskie są rozmieszczone w pamięci sekwencyjnie, w kolejności, w jakiej się pojawiają.  
  
 Klasa `NativeMethods` zawiera zestaw metod wywoływanych `App` przez klasę. Aby uzyskać szczegółowe informacje na temat przekazywania tablic, zobacz komentarze w poniższym przykładzie. Tablica, która jest typem odwołania, jest przekazywana jako in parametr domyślnie. Dla wywołującego, aby otrzymać wyniki **InAttribute** i **OutAttribute** należy jawnie zastosować do argumentu zawierającego tablicę.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Funkcje wywołujące  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Zobacz też

- [Platforma wywołuje typy danych](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
