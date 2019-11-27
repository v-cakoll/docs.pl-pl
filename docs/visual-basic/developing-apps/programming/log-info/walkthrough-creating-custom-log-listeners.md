---
title: tworzenie odbiorców dzienników niestandardowych
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353624"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Wskazówki: tworzenie odbiorników logu niestandardowego (C# i Visual Basic)

W tym instruktażu pokazano, jak utworzyć odbiornik dziennika niestandardowego i skonfigurować go do nasłuchiwania danych wyjściowych obiektu `My.Application.Log`.

## <a name="getting-started"></a>Wprowadzenie

Odbiorniki dzienników muszą dziedziczyć z klasy <xref:System.Diagnostics.TraceListener>.

#### <a name="to-create-the-listener"></a>Aby utworzyć odbiornik

- W aplikacji Utwórz klasę o nazwie `SimpleListener`, która dziedziczy po <xref:System.Diagnostics.TraceListener>.

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     Metody <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A>, wymagane przez klasę bazową, wywołują `MsgBox`, aby wyświetlić ich dane wejściowe.

     Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> jest stosowany do metod <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A>, tak aby ich atrybuty pasowały do metod klasy bazowej. Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> zezwala na hosta, na którym jest uruchamiany kod, aby określić, że kod uwidacznia synchronizację z ochroną hosta.

    > [!NOTE]
    > Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> ma zastosowanie tylko do niezarządzanych aplikacji, które obsługują środowisko uruchomieniowe języka wspólnego i implementują ochronę hosta, taką jak SQL Server.

Aby upewnić się, że `My.Application.Log` używa odbiornika dzienników, należy silnie nawiązać nazwę zestawu, który zawiera odbiornik dzienników.

Kolejna procedura zawiera kilka prostych kroków służących do tworzenia silnie nazwanego zestawu detektora dzienników. Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnej nazwie](../../../../standard/assembly/create-use-strong-named.md).

#### <a name="to-strongly-name-the-log-listener-assembly"></a>Aby silnie nawiązać nazwę zestawu odbiornika dzienników

1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** wybierz polecenie **Właściwości**.

2. Kliknij kartę **podpisywanie** .

3. Zaznacz pole **podpisz zestaw** .

4. Wybierz pozycję **\<nowe >** z listy rozwijanej **Wybierz plik klucza o silnej nazwie** .

     Zostanie otwarte okno dialogowe **Tworzenie klucza silnej nazwy** .

5. Podaj nazwę pliku klucza w polu **Nazwa pliku klucza** .

6. Wprowadź hasło w polach **Wprowadź hasło** i **Potwierdź hasło** .

7. Kliknij przycisk **OK**.

8. Skompiluj ponownie aplikację.

## <a name="adding-the-listener"></a>Dodawanie odbiornika

Teraz, gdy zestaw ma silną nazwę, należy określić silną nazwę odbiornika, tak aby `My.Application.Log` używała Twojego odbiornika dzienników.

Format silnie nazwanego typu jest następujący.

Nazwa typu \<>, \<nazwa zestawu >, \<numer wersji >, \<kultur >, \<silnej nazwy >

#### <a name="to-determine-the-strong-name-of-the-listener"></a>Aby określić silną nazwę odbiornika

- Poniższy kod pokazuje, jak określić silnie nazwanego typu dla `SimpleListener`.

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     Silna nazwa typu zależy od projektu.

Za pomocą silnej nazwy można dodać odbiornik do kolekcji `My.Application.Log` dziennika.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>Aby dodać odbiornik do My. Application. log

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     —lub—

     Jeśli istnieje plik App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Znajdź sekcję `<listeners>` w sekcji `<source>` z atrybutem `name` "DefaultSource" znajdującym się w sekcji `<sources>`. Sekcja `<sources>` znajduje się w sekcji `<system.diagnostics>` w sekcji `<configuration>` najwyższego poziomu.

3. Dodaj ten element do sekcji `<listeners>`:

    ```xml
    <add name="SimpleLog" />
    ```

4. Znajdź sekcję `<sharedListeners>` w sekcji `<system.diagnostics>` w sekcji `<configuration>` najwyższego poziomu.

5. Dodaj ten element do `<sharedListeners>` sekcji:

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     Zmień wartość `SimpleLogStrongName` na silną nazwę odbiornika.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Instrukcje: zapisywanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
