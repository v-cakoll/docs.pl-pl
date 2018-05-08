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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed2a4b91608306021ce510098eaf044520cbb089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="marshaling-different-types-of-arrays"></a>Organizowanie różnych typów tablic
Tablica jest typu odwołania w kodzie zarządzanym, który zawiera co najmniej jeden element tego samego typu. Choć tablice typów referencyjnych, są one przekazywane tak jak parametry z funkcjami niezarządzanymi. To zachowanie jest niespójny z sposób tablic są przekazywane do obiektów zarządzanych, jak we/wy parametrów. Aby uzyskać więcej informacji, zobacz [kopiowanie i przypinanie](copying-and-pinning.md).  
  
 Poniższa tabela zawiera listę opcji organizowania dla tablic oraz opis ich użycia.  
  
|Tablica|Opis|  
|-----------|-----------------|  
|Liczby całkowite przez wartość.|Przekazuje tablica liczb całkowitych jako parametr In.|  
|Liczby całkowite przez odwołanie.|Przekazuje tablica liczb całkowitych jako parametr we/wy.|  
|Liczby całkowite przez wartość (dwuwymiarowa).|Przekazuje macierzy liczb całkowitych jako parametr In.|  
|Ciągów przez wartość.|Przekazuje tablica ciągów jako parametr In.|  
|Struktur z liczbami całkowitymi.|Przekazuje tablicę struktury zawierające liczb całkowitych jako parametr In.|  
|Struktur z ciągami.|Przekazuje tablicy struktur, które zawierają tylko liczby całkowite jako parametr we/wy. Elementy członkowskie tablicy można zmieniać.|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób przekazywania następujące typy tablic:  
  
-   Tablica liczb całkowitych przez wartość.  
  
-   Tablica liczb całkowitych przez odwołanie, które można zmieniać.  
  
-   Tablica wielowymiarowa (macierz) liczb całkowitych przez wartość.  
  
-   Tablica ciągów przez wartość.  
  
-   Tablica struktury z liczbami całkowitymi.  
  
-   Tablica struktury z ciągami.  
  
 Jeśli tablica jest jawnie przekazywane przez odwołanie, domyślne zachowanie marshals tablicy jako parametr In. To zachowanie można zmienić, stosując <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> jawnie atrybutów.  
  
 Przykład tablic używa następujących funkcji niezarządzane, przedstawiono ich oryginalnej deklaracji funkcji:  
  
-   **TestArrayOfInts** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   **TestRefArrayOfInts** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   **TestMatrixOfInts** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   **TestArrayOfStrings** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   **TestArrayOfStructs** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   **TestArrayOfStructs2** wyeksportowane z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) jest niestandardowa biblioteka niezarządzane, zawierający implementacji dla funkcji wymienione wcześniej i dwie zmienne struktury, **MYPOINT** i **MYPERSON**. Struktury zawierają następujące elementy:  
  
```  
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
  
 W tym przykładzie `MyPoint` i `MyPerson` struktury zawiera osadzone typy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut ma ustawioną upewnij się, że członkowie ułożone w pamięci sekwencyjnie, w kolejności ich występowania.  
  
 `LibWrap` Klasa zawiera metody wywoływane przez zestaw `App` klasy. Aby uzyskać szczegółowe informacje na temat przekazywanie tablic należy zapoznać się z komentarzami w następującym przykładzie. Tablica, która jest typem referencyjnym, jest przekazywany jako parametr In domyślnie. Dla obiekt wywołujący, aby otrzymywać wyniki **InAttribute** i **OutAttribute** musi zostać zastosowana jawnie argument zawierający tablicy.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Zobacz też  
 [Organizowanie tablice typów](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Typy danych wywołanie platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
