---
title: 'Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 83a26f22495c849aa00143ca36b63fa147120c28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310242"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania
Mapowanie zewnętrzne pliki i pliki dbml zmodyfikujesz musi być weryfikowany pod kątem ich definicji schematu odpowiednich. Ten temat zawiera użytkowników programu Visual Studio wykonując kroki do zaimplementowania procesu weryfikacji.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>Aby sprawdzić poprawność dbml lub plik XML  
  
1. W programie Visual Studio **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **pliku**.  
  
2. W **Otwórz plik** okna dialogowego kliknij dbml lub plik mapowania XML, który chcesz zweryfikować.  
  
     Plik zostanie otwarty w **edytora XML**.  
  
3. Kliknij prawym przyciskiem myszy okno, a następnie kliknij przycisk **właściwości**.  
  
4. W **właściwości** okna, kliknij przycisk wielokropka dla **schematów** właściwości.  
  
     **Schematów XML** zostanie otwarte okno dialogowe.  
  
5. Należy zauważyć definicji schematu odpowiednie do określonych celów.  
  
    -   DbmlSchema.xsd jest definicja schematu dla sprawdzanie poprawności pliku dbml. Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd jest definicja schematu dla weryfikowania plik mapowania XML. Aby uzyskać więcej informacji, zobacz [mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6. W **użyj** kolumnę żądany schemat definicji wiersza, kliknij, aby otworzyć pole listy rozwijanej, a następnie kliknij przycisk **używają tego schematu**.  
  
     Plik definicji schematu jest teraz skojarzone z Twojej DBML lub mapowania pliku XML.  
  
     Upewnij się, że nie zaznaczono żadnych definicji schematu.  
  
7. Na **widoku** menu, kliknij przycisk **lista błędów**.  
  
     Ustal, czy zostały wygenerowane błędy, ostrzeżenia lub komunikaty. Jeśli nie, plik XML jest nieprawidłowa względem definicji schematu.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Alternatywna metoda dla podanie definicji schematu  
 Jeśli z jakiegoś powodu XSD odpowiedniego pliku nie jest wyświetlana w **schematów XML** okno dialogowe, możesz pobrać plik XSD z tematu Pomocy. Poniższe etapy ułatwiają przeprowadzenie Zapisz pobrany plik w formacie Unicode, wymagane przez edytorze XML programu Visual Studio.  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Aby skopiować plik definicji schematu z tematu Pomocy.  
  
1. Lokalizowanie tematu pomocy, który zawiera definicję schematu, zgodnie z opisem we wcześniejszej części tego tematu.  
  
    -   W przypadku plików dbml, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Aby uzyskać zewnętrznych plików mapowania, zobacz [mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2. Kliknij przycisk **Kopiuj kod** można skopiować pliku kod do Schowka.  
  
3. Uruchom program Notatnik, aby utworzyć nowy plik.  
  
4. Wklej kod ze Schowka do Notatnika.  
  
5. W programie Notatnik **pliku** menu, kliknij przycisk **Zapisz jako**.  
  
6. W **kodowanie** wybierz opcję **Unicode**.  
  
    > [!IMPORTANT]
    >  Wybranie tej opcji gwarantuje, że znacznika kolejności bajtów Unicode-16 (`FFFE`) jest dołączony do pliku tekstowego.  
  
7. W **nazwy pliku** Utwórz nazwę pliku z rozszerzeniem xsd.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
