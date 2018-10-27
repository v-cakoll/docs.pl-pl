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
ms.openlocfilehash: b0c71284fbc925aa9bb10a8bf68cef581f78d7f4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50088757"
---
# <a name="marshaling-different-types-of-arrays"></a>Organizowanie różnych typów tablic
Tablica jest typem odwołania w kodzie zarządzanym, który zawiera co najmniej jeden element tego samego typu. Mimo że tablice są typami odwołań, są one przekazywane tak jak parametry z funkcjami niezarządzanymi. To zachowanie jest niespójny z sposób zarządzanych tablic są przekazywane do obiektów zarządzanych, jak we/wy parametrów. Aby uzyskać więcej informacji, zobacz [kopiowanie i przypinanie](copying-and-pinning.md).  
  
 Poniższa tabela zawiera listę opcji marshaling dla tablic i opisano ich użycie.  
  
|Tablica|Opis|  
|-----------|-----------------|  
|Liczby całkowite przez wartość.|Przekazuje tablicę liczb całkowitych jako parametrem In.|  
|Liczby całkowite przez odwołanie.|Przekazuje tablicę liczb całkowitych jako parametr wejście/wyjście.|  
|Liczby całkowite przez wartość (dwuwymiarową).|Przekazuje macierzy liczb całkowitych jako parametrem In.|  
|Ciągów według wartości.|Przekazuje tablicę ciągów, jako parametr w.|  
|Struktury z liczbami całkowitymi.|Przekazuje tablicę struktury, które zawierają liczb całkowitych jako parametr w.|  
|Struktury z ciągami.|Przekazuje tablicę struktur, które zawierają tylko liczby całkowite jako parametr wejście/wyjście. Elementy członkowskie tablicy można zmieniać.|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak przekazać następujące typy tablic:  
  
-   Tablica liczb całkowitych przez wartość.  
  
-   Tablica liczb całkowitych według odwołania, którego rozmiar można zmieniać.  
  
-   Tablica wielowymiarowa (macierzy) liczb całkowitych przez wartość.  
  
-   Tablica ciągów według wartości.  
  
-   Tablica struktury z liczbami całkowitymi.  
  
-   Tablica struktury z ciągami.  
  
 Jeśli tablica jest jawnie organizowane przez odwołanie, domyślne zachowanie kieruje tablicę jako parametr w. Można zmienić to zachowanie, stosując <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> jawnie atrybutów.  
  
 Przykłady tablic używa następujących funkcji niezarządzanych, wyświetlane wraz z ich oryginalną deklaracją funkcji:  
  
-   **TestArrayOfInts** eksportowany z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   **TestRefArrayOfInts** eksportowany z PinvokeLib.dll.  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   **TestMatrixOfInts** eksportowany z PinvokeLib.dll.  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   **TestArrayOfStrings** eksportowany z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   **TestArrayOfStructs** eksportowany z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   **TestArrayOfStructs2** eksportowany z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) jest niestandardową biblioteką niezarządzaną, która zawiera implementacje dla wyżej wymienionych funkcji i dwie zmienne struktury, **MYPOINT** i **MYPERSON**. Struktury zawierają następujące elementy:  
  
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
  
 W tym przykładzie `MyPoint` i `MyPerson` struktury zawierają typów osadzonych. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Ma ustawioną wartość atrybutu upewnij się, że elementy członkowskie są rozmieszczone w pamięci sekwencyjnej, w kolejności, w jakiej są wyświetlane.  
  
 `LibWrap` Klasa zawiera metody wywoływane przez zbiór `App` klasy. Aby uzyskać szczegółowe informacje na temat przekazywania tablic Zobacz komentarze w następującym przykładzie. Tablica, która jest typem odwołania, jest przekazywany jako parametr w domyślnie. Do obiektu wywołującego do odbierania wyników **InAttribute** i **OutAttribute** muszą być jawnie stosowane do argumentu zawierający tablicę.  
  
### <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Zobacz też  
 [Organizowanie tablic typów](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Typy danych w wywołaniu platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
