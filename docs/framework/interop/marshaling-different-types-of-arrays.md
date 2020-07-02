---
title: Organizowanie różnych typów tablic
description: Kierowanie różnych typów tablicowych, takich jak liczby całkowite według wartości lub odwołania, 2-wymiarowe liczby całkowite według wartości, ciągów według wartości oraz struktur z liczbami całkowitymi lub ciągami.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621499"
---
# <a name="marshaling-different-types-of-arrays"></a>Organizowanie różnych typów tablic
Tablica jest typem referencyjnym w zarządzanym kodzie, który zawiera co najmniej jeden element tego samego typu. Chociaż tablice są typami odwołań, są one przesyłane jako parametry do funkcji niezarządzanych. To zachowanie jest niespójne w sposób, w jaki zarządzane tablice są przesyłane do zarządzanych obiektów, które są jako parametry wejściowe/out. Aby uzyskać więcej informacji, zobacz [kopiowanie i Przypinanie](copying-and-pinning.md).  
  
 W poniższej tabeli wymieniono opcje organizowania dla tablic i opisano ich użycie.  
  
|Tablica|Opis|  
|-----------|-----------------|  
|Liczby całkowite według wartości.|Przekazuje tablicę liczb całkowitych jako parametr in.|  
|Liczb całkowitych przez odwołanie.|Przekazuje tablicę liczb całkowitych jako parametr we/out.|  
|Liczby całkowite przez wartość (dwuwymiarowe).|Przekazuje tablicę liczb całkowitych jako parametr in.|  
|Ciągów według wartości.|Przekazuje tablicę ciągów jako parametr.|  
|Struktur z liczbami całkowitymi.|Przekazuje tablicę struktur, które zawierają liczby całkowite jako parametr in.|  
|Struktur z ciągami.|Przekazuje tablicę struktur, które zawierają tylko ciągi jako parametr in/out. Elementy członkowskie tablicy można zmienić.|  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak przekazać następujące typy tablic:  
  
- Tablica liczb całkowitych według wartości.  
  
- Tablica liczb całkowitych według odwołania, które mogą być zmieniane.  
  
- Tablica wielowymiarowa (macierz) liczb całkowitych według wartości.  
  
- Tablica ciągów według wartości.  
  
- Tablica struktur z liczbami całkowitymi.  
  
- Tablica struktur z ciągami.  
  
 Jeśli tablica nie jest jawnie organizowana przez odwołanie, zachowanie domyślne służy do organizowania tablicy jako parametru in. To zachowanie można zmienić, stosując <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> jawnie atrybuty i.  
  
 Przykłady tablic używają następujących funkcji niezarządzanych, które są wyświetlane wraz z ich oryginalną deklaracją funkcji:  
  
- **TestArrayOfInts** wyeksportowany z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- **TestRefArrayOfInts** wyeksportowany z PinvokeLib.dll.  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- **TestMatrixOfInts** wyeksportowany z PinvokeLib.dll.  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- **TestArrayOfStrings** wyeksportowany z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- **TestArrayOfStructs** wyeksportowany z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- **TestArrayOfStructs2** wyeksportowany z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementacje wcześniej wymienionych funkcji oraz dwie zmienne **struktury, "** i **".** Struktury zawierają następujące elementy:  
  
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
  
 W tym przykładzie `MyPoint` `MyPerson` struktury i zawierają osadzone typy. <xref:System.Runtime.InteropServices.StructLayoutAttribute>Atrybut jest ustawiony tak, aby upewnić się, że elementy członkowskie są ułożone w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.  
  
 `NativeMethods`Klasa zawiera zestaw metod wywoływanych przez `App` klasę. Aby uzyskać szczegółowe informacje dotyczące przekazywania tablic, zobacz komentarze w poniższym przykładzie. Tablica, która jest typem referencyjnym, jest domyślnie przenoszona jako parametr in. Aby obiekt wywołujący otrzymywał wyniki, należy zastosować jawny **atrybut** i atrybut **Attribute** do argumentu zawierającego tablicę.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych wywołania platformy](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
