---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: cc299e26316b1a3a6fd9b475dcdb8e3911bcf2e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356331"
---
# <a name="serialization"></a>Serializacja
W tym temacie opisano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] możliwości serializacji. Sekcjach poniżej zawierają informacje o sposobie dodawania serializacji podczas generowania kodu w czasie projektowania i zachowania czasu wykonywania serializacji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] klasy.  
  
 Można dodać kodu serializacji w czasie projektowania, przy użyciu jednej z następujących metod:  
  
-   W [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], zmień **tryb serializacji** właściwości **Unidirectional**.  
  
-   W wierszu polecenia SQLMetal dodać **/serialization** opcji. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Omówienie  
 Kod wygenerowany przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia możliwości ładowanie odłożone domyślnie. Ładowanie odłożone jest bardzo wygodny w warstwie pośredniej przezroczysty podczas ładowania danych na żądanie. Warto jednak powodować problemy dla serializacji, ponieważ serializator wyzwala odroczonego ładowania, czy ładowanie odłożone jest przeznaczone. W efekcie podczas serializowany jest obiekt, jego zamknięcia przechodnie w obszarze wszystkie wychodzące odwołania mają być odroczone załadowanych jest serializowany.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Funkcji serializacji rozwiązuje ten problem, przede wszystkim za pomocą dwóch mechanizmów:  
  
-   A <xref:System.Data.Linq.DataContext> tryb wyłączenie odroczonego ładowania (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.DataContext>.  
  
-   Przełącznik generowania kodu, aby wygenerować <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> i <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atrybuty w wygenerowanym jednostek. Ten aspekt zachowanie odroczenie ładowania klas w serializacji, w tym podlega głównych w tym temacie.  
  
### <a name="definitions"></a>Definicje  
  
-   *Serializator DataContract*: domyślna serializator używany przez składnik usług Windows Communication Framework (WCF) programu .NET Framework 3.0 lub nowszej wersji.  
  
-   *Jednokierunkowe serializacji*: wersja po serializacji jest klasy, która zawiera tylko właściwość skojarzenie jednokierunkowe (w celu uniknięcia cykl). Konwencja właściwość po stronie nadrzędnej relacji klucza obcego podstawowy jest oznaczony do serializacji. Nie jest serializowany drugiej stronie skojarzenia dwukierunkowego.  
  
     Serializacja jednokierunkowe jest jedynym typem serializacji obsługiwane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="code-example"></a>Przykład kodu  
 W poniższym kodzie użyto tradycyjne `Customer` i `Order` klasy z przykładowej bazy danych Northwind i pokazuje, jak te klasy ozdobione atrybutów serializacji.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 Dla `Order` klasy w poniższym przykładzie, tylko właściwość skojarzenie wsteczne odpowiadający `Customer` klasy jest wyświetlany w celu jego skrócenia. Nie ma `DataMember` atrybutu, aby uniknąć cyklu.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Jak do serializacji jednostek.  
 Może wykonywać serializację jednostek w kodzie pokazano w poprzedniej sekcji  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Relacje cykliczne samoobsługowego  
 Relacje cykliczne samoobsługowego wykonują te same czynności. Nie ma właściwości skojarzenia odpowiadający klucz obcy `DataMember` atrybutu właściwość nadrzędna nie.  
  
 Należy wziąć pod uwagę następujące klasy, która ma dwie relacje cykliczne samoobsługowego: Employee.Manager/Reports i Employee.Mentor/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Instrukcje: Umożliwianie serializacji jednostek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
