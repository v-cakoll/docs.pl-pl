---
title: tworzenie odbiorców dzienników niestandardowych
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353624"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Wskazówki: tworzenie odbiorników logu niestandardowego (C# i Visual Basic)

W tym przewodniku pokazano, jak utworzyć odbiornik dziennika niestandardowego i skonfigurować `My.Application.Log` go do nasłuchiwać danych wyjściowych obiektu.

## <a name="getting-started"></a>Wprowadzenie

Detektory dziennika musi <xref:System.Diagnostics.TraceListener> dziedziczyć z klasy.

#### <a name="to-create-the-listener"></a>Aby utworzyć odbiornik

- W aplikacji utwórz klasę `SimpleListener` o nazwie, która dziedziczy po <xref:System.Diagnostics.TraceListener>.

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     I <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody, wymagane przez klasę podstawową, wywołać, `MsgBox` aby wyświetlić ich dane wejściowe.

     Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> jest stosowany do <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody, tak aby ich atrybuty zgodne z metody klasy podstawowej. Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> umożliwia hostowi, który uruchamia kod, aby ustalić, że kod udostępnia synchronizację ochrony hosta.

    > [!NOTE]
    > Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> jest skuteczny tylko w przypadku niezarządzanych aplikacji, które hostują środowisko uruchomieniowe języka wspólnego i które implementują ochronę hosta, takich jak SQL Server.

Aby upewnić się, że `My.Application.Log` używa odbiornika dziennika, należy zdecydowanie nazwa zestawu, który zawiera odbiornika dziennika.

Następna procedura zawiera kilka prostych kroków do tworzenia zestawu odbiornika dziennika o silnie nazwanej. Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../../standard/assembly/create-use-strong-named.md).

#### <a name="to-strongly-name-the-log-listener-assembly"></a>Aby zdecydowanie nazwać zestaw detektora dziennika

1. Wybierz projekt w **Eksploratorze rozwiązań**. W menu **Projekt** wybierz polecenie **Właściwości**.

2. Kliknij kartę **Podpisywanie.**

3. Zaznacz pole **Podpisz złożenie.**

4. Wybierz ** \<pozycję Nowy>** z listy **rozwijanej Wybierz plik klucza silnej nazwy.**

     Zostanie otwarte okno dialogowe **Tworzenie klucza silnej nazwy.**

5. Podaj nazwę pliku klucza w polu **Nazwa pliku klucza.**

6. Wprowadź hasło w polach **Wprowadź hasło** i **Potwierdź hasło.**

7. Kliknij przycisk **OK**.

8. Odbuduj aplikację.

## <a name="adding-the-listener"></a>Dodawanie odbiornika

Teraz, gdy zestaw ma silną nazwę, należy określić silną `My.Application.Log` nazwę odbiornika, tak aby używa odbiornika dziennika.

Format typu o silnie nazwanym jest następujący.

\<> nazwa typu, \<> nazwa zestawu, \<numer wersji>, \<> kultury, \<>

#### <a name="to-determine-the-strong-name-of-the-listener"></a>Aby określić silną nazwę odbiornika

- Poniższy kod pokazuje, jak określić `SimpleListener`nazwę typu o silnie nazwanej dla .

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     Silna nazwa typu zależy od projektu.

Dzięki silnej nazwie można dodać odbiornik `My.Application.Log` do kolekcji detektora dziennika.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>Aby dodać odbiornik do My.Application.Log

1. Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz pozycję **Otwórz**.

     — lub —

     Jeśli istnieje plik app.config:

    1. W menu **Projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Znajdź `<listeners>` sekcję w `<source>` sekcji `name` z atrybutem "DefaultSource", `<sources>` znajdującym się w sekcji. Sekcja `<sources>` znajduje się `<system.diagnostics>` w sekcji, w `<configuration>` sekcji najwyższego poziomu.

3. Dodaj ten element `<listeners>` do sekcji:

    ```xml
    <add name="SimpleLog" />
    ```

4. Zlokalizuj `<sharedListeners>` `<system.diagnostics>` sekcję w sekcji `<configuration>` w sekcji najwyższego poziomu.

5. Dodaj ten element `<sharedListeners>` do tej sekcji:

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     Zmień `SimpleLogStrongName` wartość, aby być silną nazwą odbiornika.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Porady: wyjątki rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Porady: zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
