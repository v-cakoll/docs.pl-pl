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

W tym instruktażu pokazano, jak utworzyć odbiornik dziennika niestandardowego i skonfigurować go do nasłuchiwania danych wyjściowych `My.Application.Log` obiektu.

## <a name="getting-started"></a>Getting Started

Odbiorniki dzienników muszą dziedziczyć <xref:System.Diagnostics.TraceListener> z klasy.

#### <a name="to-create-the-listener"></a>Aby utworzyć odbiornik

- W aplikacji Utwórz klasę o nazwie `SimpleListener` , która dziedziczy z. <xref:System.Diagnostics.TraceListener>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     Metody <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> , wymagane przez klasę bazową, wywołują `MsgBox` , aby wyświetlić ich dane wejściowe.

     Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut jest stosowany do metod <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> , tak aby ich atrybuty pasowały do metod klasy bazowej. Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut zezwala na hosta, na którym jest uruchamiany kod, aby określić, że kod uwidacznia synchronizację z ochroną hosta.

    > [!NOTE]
    > Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut obowiązuje tylko w przypadku niezarządzanych aplikacji obsługujących środowisko uruchomieniowe języka wspólnego i implementujących ochronę hosta, takich jak SQL Server.

Aby zapewnić, `My.Application.Log` że program korzysta z odbiornika dzienników, należy silnie nawiązać nazwę zestawu, który zawiera odbiornik dzienników.

Kolejna procedura zawiera kilka prostych kroków służących do tworzenia silnie nazwanego zestawu detektora dzienników. Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnej nazwie](../../../../standard/assembly/create-use-strong-named.md).

#### <a name="to-strongly-name-the-log-listener-assembly"></a>Aby silnie nawiązać nazwę zestawu odbiornika dzienników

1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** wybierz polecenie **Właściwości**.

2. Kliknij kartę **podpisywanie** .

3. Zaznacz pole **podpisz zestaw** .

4. Wybierz pozycję ** \<nowy>** z listy rozwijanej **Wybierz plik klucza o silnej nazwie** .

     Zostanie otwarte okno dialogowe **Tworzenie klucza silnej nazwy** .

5. Podaj nazwę pliku klucza w polu **Nazwa pliku klucza** .

6. Wprowadź hasło w polach **Wprowadź hasło** i **Potwierdź hasło** .

7. Kliknij przycisk **OK**.

8. Skompiluj ponownie aplikację.

## <a name="adding-the-listener"></a>Dodawanie odbiornika

Teraz, gdy zestaw ma silną nazwę, należy określić silną nazwę odbiornika, aby `My.Application.Log` używała odbiornika dzienników.

Format silnie nazwanego typu jest następujący.

\<Nazwa typu>, \<nazwa zestawu>, \<numer wersji>, \<kultura>, \<silna nazwa>

#### <a name="to-determine-the-strong-name-of-the-listener"></a>Aby określić silną nazwę odbiornika

- Poniższy kod pokazuje, jak określić silną nazwę typu dla `SimpleListener`.

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     Silna nazwa typu zależy od projektu.

Za pomocą silnej nazwy można dodać odbiornik do kolekcji detektorów `My.Application.Log` dzienników.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>Aby dodać odbiornik do My. Application. log

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     — lub —

     Jeśli istnieje plik App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij pozycję **Add** (Dodaj).

2. Znajdź `<listeners>` sekcję w `<source>` sekcji z `name` atrybutem "DefaultSource", który znajduje się w `<sources>` sekcji. `<sources>` Sekcja znajduje się w `<system.diagnostics>` sekcji w sekcji najwyższego poziomu `<configuration>` .

3. Dodaj ten element do `<listeners>` sekcji:

    ```xml
    <add name="SimpleLog" />
    ```

4. Znajdź `<sharedListeners>` sekcję `<system.diagnostics>` w sekcji, w sekcji najwyższego poziomu `<configuration>` .

5. Dodaj ten element do tej `<sharedListeners>` sekcji:

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     Zmień wartość tak, `SimpleLogStrongName` aby była silną nazwą odbiornika.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: rejestrowanie wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Instrukcje: zapisywanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
