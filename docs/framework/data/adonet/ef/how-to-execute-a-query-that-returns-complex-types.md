---
title: 'Porady: wykonywanie zapytania, które zwraca typy złożone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 013f1980d2ea13927871719aeea293cfce38b4d5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385310"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Porady: wykonywanie zapytania, które zwraca typy złożone
W tym temacie przedstawiono sposób wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytanie, które zwraca jednostki typu obiektów, które zawierają właściwość typu złożonego.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1.  Dodaj [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreator modelu Entity Data Model](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Kliknij dwukrotnie plik edmx, aby wyświetlić model w [okna przeglądarki modelu](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) Projektant jednostki. Na powierzchni projektanta jednostki wybierz `Email` i `Phone` właściwości `Contact` typu jednostki, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **refaktoryzacji na nowy typ złożony**.  
  
4.  Nowy typ złożony z wybranym `Email` i `Phone` właściwości jest dodawany do **przeglądarka modeli**. Typ złożony jest nadawana nazwa domyślna: zmiana nazwy typu, który ma `EmailPhone` w **właściwości** okna. Ponadto nowy `ComplexProperty` właściwość została dodana do `Contact` typu jednostki. Zmień nazwę właściwości do `EmailPhoneComplexType.`  
  
     Uzyskać informacji o tworzeniu i modyfikowaniu złożonych typów za pomocą Kreator modelu Entity Data Model, zobacz [jak: Refaktoryzuj istniejących właściwości do właściwości złożonej typu](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) i [jak: tworzenie i modyfikowanie typów złożonych](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje zapytanie, które zwraca kolekcję `Contact` obiektów i zostaną wyświetlone dwie właściwości `Contact` obiektów: `ContactID` i wartości `EmailPhoneComplexType` typu złożonego.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
