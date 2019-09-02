---
title: Elementy DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203821"
---
# <a name="datatablereaders"></a>Elementy DataTableReader
Przedstawia zawartość a <xref:System.Data.DataTable> lub a <xref:System.Data.DataSet> w postaci co najmniej jednego zestawu wyników tylko do odczytu. <xref:System.Data.DataTableReader>  
  
 Po utworzeniu **DataTableReader** z **tabeli DataTable**wynikowy obiekt **DataTableReader** zawiera jeden zestaw wyników z tymi samymi danymi co element **DataTable** , z którego został utworzony, z wyjątkiem wierszy, które zostały oznaczone jako skasowan. Kolumny są wyświetlane w takiej samej kolejności jak w oryginalnej **tabeli DataTable**.  
  
 **DataTableReader** może zawierać wiele zestawów wyników, jeśli został utworzony przez wywołanie <xref:System.Data.DataSet.CreateDataReader%2A>. Wyniki znajdują się w takiej samej kolejności jak w **tabelach** **danych** w <xref:System.Data.DataSet.Tables%2A> kolekcji obiektów DataSet.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementu DataReader](creating-a-datareader.md)  
 W tym artykule omówiono sposób tworzenia obiektu **DataTableReader** .  
  
 [Nawigowanie w elementach DataTable](navigating-datatables.md)  
 Opisuje użycie metody **Read** , aby przejść przez zawartość **DataTableReader**.  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](../retrieving-and-modifying-data.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
