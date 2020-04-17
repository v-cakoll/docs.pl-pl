---
title: Instalowanie platformy .NET for Apache Spark w notesach jupyter w klastrach platformy Azure HDInsight Spark
description: Dowiedz się, jak zainstalować program .NET for Apache Spark w notesach jupyter usługi Azure HDInsight.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 953bffe5f6ec56cd0adf4224afd2eedfe0001aa9
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607418"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Instalowanie platformy .NET for Apache Spark w notesach jupyter w klastrach platformy Azure HDInsight Spark

W tym artykule dowiesz się, jak zainstalować program .NET for Apache Spark w notesach jupyter w klastrach platformy Azure HDInsight Spark. Program .NET for Apache Spark można wdrożyć w klastrach usługi Azure HDInsight za pomocą kombinacji wiersza polecenia i portalu Azure (aby uzyskać więcej informacji, zobacz [jak wdrożyć aplikację platformy .NET for Apache Spark w usłudze Azure HDInsight),](../tutorials/hdinsight-deployment.md)ale notesy zapewniają bardziej interaktywne i iteracyjne środowisko.

Klastry usługi Azure HDInsight są już wyposażone w notesy Jupyter, więc wszystko, co musisz zrobić, to skonfigurować notesy Jupyter do uruchamiania platformy .NET dla platformy Spark apache. Aby użyć platformy .NET for Apache Spark w notesach jupyter, potrzebny jest wartość REPL języka C# do wykonania wiersza według wiersza kodu języka C# i zachowania stanu wykonania w razie potrzeby. [Try .NET](https://github.com/dotnet/try) został zintegrowany jako oficjalny .NET REPL.

Aby włączyć program .NET for Apache Spark za pośrednictwem obsługi notesów Jupyter, należy wykonać kilka ręcznych kroków za pomocą [programu Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) i przesłać [akcje skryptu](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) w klastrze platformy SPARK usługi HDInsight.

> [!NOTE]
> Ta funkcja jest *eksperymentalna* i nie jest obsługiwana przez zespół HDInsight Spark.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jeszcze go nie masz, utwórz klaster [platformy Azure HDInsight Spark.](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight)

1. Odwiedź [witrynę Azure portal](https://portal.azure.com) i wybierz **pozycję + Utwórz zasób**.

1. Utwórz nowy zasób klastra usługi Azure HDInsight. Wybierz **Spark 2.4** i **HDI 4.0** podczas tworzenia klastra.

## <a name="install-net-for-apache-spark"></a>Instalowanie platformy .NET dla platformy Spark

W witrynie Azure portal wybierz **klaster platformy SPARK usługi HDInsight** utworzony w poprzednim kroku.

### <a name="stop-the-livy-server"></a>Zatrzymaj serwer Livy

1. W portalu wybierz **pozycję Przegląd**, a następnie wybierz pozycję **Ambari home**. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia logowania dla klastra.

   ![Zatrzymaj livy server](./media/hdinsight-notebook-installation/select-ambari.png)

2. Z lewego menu nawigacji wybierz **opcję Spark2** i wybierz opcję **LIVY FOR SPARK2 SERVER**.

   ![Zatrzymaj livy server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. Wybierz **hn0... hosta**.

   ![Zatrzymaj livy server](./media/hdinsight-notebook-installation/select-host.png)

4. Wybierz wielokropek obok **pozycji Livy for Spark2 Server** i wybierz pozycję **Zatrzymaj**. Po wyświetleniu monitu wybierz przycisk **OK,** aby kontynuować.

   Zatrzymaj Livy dla serwera Spark2.
   ![Zatrzymaj livy server](./media/hdinsight-notebook-installation/stop-server.png)

5. Powtórz poprzednie kroki dla **hn1... hosta**.

### <a name="submit-an-hdinsight-script-action"></a>Przesyłanie akcji skryptu HDInsight

1. Jest `install-interactive-notebook.sh` to skrypt, który instaluje .NET dla Apache Spark i wprowadza zmiany do Apache Livy i sparkmagic. Przed przesłaniem akcji skryptu do pliku HDInsight `install-interactive-notebook.sh`należy utworzyć i przesłać plik .

   Utwórz nowy plik o nazwie **install-interactive-notebook.sh** na komputerze lokalnym i wklej zawartość [install-interactive-notebook.sh zawartości](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).

   Przekaż skrypt do identyfikatora [URI,](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) który jest dostępny z klastra HDInsight. Na przykład `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. Uruchom `install-interactive-notebook.sh` w klastrze przy użyciu [akcji skryptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

   Wróć do klastra HDI w witrynie Azure portal i wybierz **akcje skryptu** z opcji po lewej stronie. Prześlij jedną akcję skryptu, aby wdrożyć .NET for Apache Spark REPL w klastrze platformy SPARK usługi HDInsight. Użyj następujących ustawień:

   |Właściwość  |Opis  |
   |---------|---------|
   | Typ skryptu | Niestandardowy |
   | Nazwa | *Instalowanie programu .NET dla interaktywnego notebooka Apache Spark* |
   | Identyfikator URI skryptu bash | Identyfikator URI, do `install-interactive-notebook.sh`którego został przesłany . |
   | Typy węzłów| Głowa i pracownik |
   | Parametry | .NET dla wersji Apache Spark. Możesz sprawdzić [.NET dla apache Spark wydań](https://github.com/dotnet/spark/releases). Na przykład, jeśli chcesz zainstalować Sparkdotnet w wersji 0.6.0 to będzie `0.6.0`.

   Przejdź do następnego kroku, gdy obok stanu akcji skryptu pojawią się zielone znaczniki wyboru.

### <a name="start-the-livy-server"></a>Uruchamianie serwera Livy

Postępuj zgodnie z instrukcjami w sekcji [Zatrzymaj serwer Livy,](#stop-the-livy-server) aby **uruchomić** (a nie **zatrzymać)** serwer Livy dla Spark2 dla hostów **hn0** i **hn1.**

### <a name="set-up-spark-default-configurations"></a>Konfigurowanie domyślnych konfiguracji platformy Spark

1. W portalu wybierz **pozycję Przegląd**, a następnie wybierz pozycję **Ambari home**. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia logowania dla klastra.

2. Wybierz **Spark2** i **CONFIGS**. Następnie wybierz pozycję **Niestandardowe iskrzenie2-domyślne**.

   ![Ustawianie konfiguracji](./media/hdinsight-notebook-installation/spark-configs.png)

3. Wybierz **pozycję Dodaj właściwość...,** aby dodać domyślne ustawienia platformy Spark.

   ![Dodaj właściwość](./media/hdinsight-notebook-installation/add-property.png)

   Istnieją trzy indywidualne właściwości. Dodaj je pojedynczo przy użyciu text typu **właściwości** w trybie dodawania właściwości Single. Sprawdź, czy nie masz żadnych dodatkowych spacji przed lub po żadnym z kluczy /wartości.

   * **Nieruchomość 1**
       * Klucz:&ensp;&ensp;`spark.dotnet.shell.command`
       * Wartość:`/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Nieruchomość 2** Użyj wersji platformy .NET dla platformy Apache Spark, która została uwzględniona w poprzedniej akcji skryptu.
       * Klucz:&ensp;&ensp;`spark.dotnet.packages`
       * Wartość:`["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **Nieruchomość 3**
       * Klucz:&ensp;&ensp;`spark.dotnet.interpreter`
       * Wartość:`try`

   Na przykład poniższy obraz przechwytuje ustawienie dodawania właściwości 1:

   ![Ustawianie konfiguracji](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Po dodaniu trzech właściwości wybierz pozycję **ZAPISZ**. Jeśli widzisz ekran ostrzegawczy rekomendacji konfigura, wybierz **PROCEED ANYWAY**.

4. Uruchom ponownie składniki, których dotyczy problem.

   Po dodaniu nowych właściwości należy ponownie uruchomić składniki, których zmiany miały wpływ. U góry wybierz pozycję **RESTART**, a następnie **uruchom ponownie wszystkie, których dotyczy problem** z listy rozwijanej.

   ![Ustawianie konfiguracji](./media/hdinsight-notebook-installation/restart-affected.png)

   Po wyświetleniu monitu wybierz pozycję **POTWIERDŹ PONOWNIE WSZYSTKO,** aby kontynuować, a następnie kliknij przycisk **OK,** aby zakończyć.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Przesyłanie zadań za pośrednictwem notesu Jupyter

Po zakończeniu poprzednich kroków można teraz przesłać zadania platformy .NET dla platformy Apache Spark za pośrednictwem notesów Jupyter.

1. Utwórz nowy notes platformy .NET dla platformy Apache Spark. Uruchom notes Jupyter z klastra HDI w witrynie Azure portal.

   ![Uruchom notebook Jupyter](./media/hdinsight-notebook-installation/launch-notebook.png)

   Następnie wybierz pozycję **Nowa** > **platforma Iskrowa .NET (C#),** aby utworzyć notes.

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Prześlij zadania przy użyciu platformy .NET for Apache Spark.

   Użyj następującego fragmentu kodu, aby utworzyć ramkę DataFrame:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Prześlij zadanie spark](./media/hdinsight-notebook-installation/create-df.png)

   Użyj następującego fragmentu kodu, aby zarejestrować funkcję zdefiniowaną przez użytkownika (UDF) i użyć UDF z dataframes:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Prześlij zadanie spark](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Następne kroki

* [Wdrażanie aplikacji platformy .NET dla platformy Spark usługi Apache w usłudze Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Dokumentacja hdinsight](https://docs.microsoft.com/azure/hdinsight/)
