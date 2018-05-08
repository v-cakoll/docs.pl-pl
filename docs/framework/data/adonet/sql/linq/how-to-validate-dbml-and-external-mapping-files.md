---
title: 'Porady: Sprawdzanie poprawności DBML i plikami zewnętrznych mapowania'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 9bf21353aebd0ae57c51b2ddf3b31b5e7f1ac615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Porady: Sprawdzanie poprawności DBML i plikami zewnętrznych mapowania
Mapowanie zewnętrzne pliki i pliki .dbml zmodyfikowaniu musi zostać zweryfikowany względem ich definicje odpowiednich schematu. Ten temat zawiera użytkowników programu Visual Studio czynności do wykonania procesu weryfikacji.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>Aby sprawdzić poprawność pliku XML lub .dbml  
  
1.  W programie Visual Studio **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **pliku**.  
  
2.  W **Otwórz plik** okna dialogowego kliknij .dbml lub plik mapowania XML, który chcesz zweryfikować.  
  
     Otwiera plik w **edytora XML**.  
  
3.  Kliknij prawym przyciskiem myszy okna, a następnie kliknij przycisk **właściwości**.  
  
4.  W **właściwości** okna, kliknij przycisk wielokropka dla **schematy** właściwości.  
  
     **Schematów XML** zostanie otwarte okno dialogowe.  
  
5.  Należy zwrócić uwagę definicji schematu odpowiednie do określonych celów.  
  
    -   DbmlSchema.xsd jest sprawdzanie poprawności pliku .dbml definicję schematu. Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd jest definicji schematu do zweryfikowania plik mapowania XML. Aby uzyskać więcej informacji, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  W **użyj** kolumnę żądany schemat definicji wiersza, kliknij, aby otworzyć okno listy rozwijanej, a następnie kliknij przycisk **używają tego schematu**.  
  
     Plik definicji schematu jest teraz skojarzone z Twojej DBML lub XML w pliku mapowania.  
  
     Upewnij się, że nie wybrano żadnych definicji schematu.  
  
7.  Na **widoku** menu, kliknij przycisk **listy błędów**.  
  
     Ustal, czy zostały wygenerowane błędy, ostrzeżenia lub komunikaty. Jeśli nie, plik XML jest nieprawidłowa względem definicji schematu.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Alternatywna metoda w dostarczaniu definicji schematu  
 Jeśli zaistnieje odpowiednie XSD pliku nie ma w **schematów XML** okno dialogowe, możesz pobrać plik XSD z tematu Pomocy. Poniższe etapy ułatwiają Zapisz pobrany plik w formacie Unicode, wymagane edytora XML w Visual Studio.  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Aby skopiować plik definicji schematu z tematu Pomocy.  
  
1.  Lokalizowanie tematu pomocy, który zawiera definicję schematu, zgodnie z opisem we wcześniejszej części tego tematu.  
  
    -   W przypadku plików .dbml, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Dla zewnętrznych mapowania plików, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Kliknij przycisk **Kopiuj kod** można skopiować pliku kodu do Schowka.  
  
3.  Uruchom program Notatnik, aby utworzyć nowy plik.  
  
4.  Wklej kod ze Schowka do Notatnika.  
  
5.  W programie Notatnik **pliku** menu, kliknij przycisk **Zapisz jako**.  
  
6.  W **kodowanie** wybierz opcję **Unicode**.  
  
    > [!IMPORTANT]
    >  Wybranie tej opcji gwarantuje, że znacznik kolejności bajtów Unicode-16 (`FFFE`) jest dołączany na początku w pliku tekstowym.  
  
7.  W **nazwę pliku** Utwórz nazwę pliku z rozszerzeniem xsd.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
