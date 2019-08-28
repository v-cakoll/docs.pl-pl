---
title: 'Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 212d65dfe998b825dd40e564756083ed685dff6f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041132"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania

Pliki mapowania zewnętrznego i pliki. dbml, które należy zmodyfikować, muszą być zweryfikowane pod kątem odpowiednich definicji schematu. Ten temat zawiera informacje o użytkownikach programu Visual Studio z krokami w celu zaimplementowania procesu walidacji.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a>Aby sprawdzić poprawność pliku. dbml lub XML

1. W menu **plik** programu Visual Studio wskaż polecenie **Otwórz**, a następnie kliknij pozycję **plik**.

2. W oknie dialogowym **Otwórz plik** kliknij plik mapowania dbml lub XML, który chcesz zweryfikować.

    Plik zostanie otwarty w **edytorze XML**.

3. Kliknij okno prawym przyciskiem myszy, a następnie kliknij polecenie **Właściwości**.

4. W oknie **Właściwości** kliknij wielokropek dla właściwości **schematy** .

    Zostanie otwarte okno dialogowe **schematy XML** .

5. Zanotuj odpowiednią definicję schematu dla danego celu.

    - DbmlSchema. xsd jest definicją schematu służącą do walidacji pliku. dbml. Aby uzyskać więcej informacji, zobacz [generowanie kodu w LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - LinqToSqlMapping. xsd jest definicją schematu służącą do walidacji zewnętrznego pliku mapowania XML. Aby uzyskać więcej informacji, zobacz [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

6. W kolumnie **Użyj** w żądanym wierszu definicji schematu kliknij, aby otworzyć pole listy rozwijanej, a następnie kliknij pozycję **Użyj tego schematu**.

    Plik definicji schematu jest teraz skojarzony z plikiem mapowania DBML lub XML.

    Upewnij się, że nie wybrano żadnych innych definicji schematu.

7. W menu **Widok** kliknij **Lista błędów**.

    Należy określić, czy zostały wygenerowane błędy, ostrzeżenia lub komunikaty. W przeciwnym razie plik XML jest prawidłowy względem definicji schematu.

## <a name="alternate-method-for-supplying-schema-definition"></a>Alternatywna metoda dostarczania definicji schematu

Jeśli z jakiegoś powodu odpowiedni plik XSD nie jest wyświetlany w oknie dialogowym **schematy XML** , można pobrać plik XSD z tematu pomocy. Poniższe kroki ułatwiają zapisanie pobranego pliku w formacie Unicode wymaganym przez Edytor XML programu Visual Studio.

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Aby skopiować plik definicji schematu z tematu pomocy

1. Znajdź temat pomocy zawierający definicję schematu, jak opisano wcześniej w tym temacie.

    - Aby uzyskać pliki. dbml, zobacz [generowanie kodu w LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - W przypadku zewnętrznych plików mapowania zobacz [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

2. Kliknij przycisk **Kopiuj kod** , aby skopiować plik kodu do Schowka.

3. Uruchom Notatnik, aby utworzyć nowy plik.

4. Wklej kod ze schowka do pliku Notatnika.

5. W menu **plik** Notatnika kliknij przycisk **Zapisz jako**.

6. W polu **kodowanie** wybierz opcję **Unicode**.

    > [!IMPORTANT]
    > Wybranie tej opcji gwarantuje, że znacznik kolejności bajtów Unicode-16 (`FFFE`) jest poprzedzony plikiem tekstowym.

7. W polu **Nazwa pliku** Utwórz nazwę pliku z rozszerzeniem XSD.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
