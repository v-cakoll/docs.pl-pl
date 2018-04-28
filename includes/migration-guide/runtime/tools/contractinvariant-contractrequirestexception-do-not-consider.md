### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant lub Contract.Requires<TException> nie należy traktować String.IsNullOrEmpty jako czysty

|   |   |
|---|---|
|Szczegóły|Dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.1, jeśli niezmiennej kontraktu dla <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> lub kontrakt warunek wstępny dla <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> wywołania <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody funkcji ponownego zapisu emituje kompilatora ostrzeżenie CC1036: &quot;Wykryto wywołanie metody " System.String.IsNullOrWhteSpace(System.String) "bez [czystej] w metodzie.&quot; To ostrzeżenie, a nie wystąpi błąd kompilatora kompilatora.|
|Sugestia|To zachowanie zostało rozwiązane w [GitHub problem #339](https://github.com/Microsoft/CodeContracts/issues/339). Aby usunąć to ostrzeżenie, możesz pobrać i skompilować zaktualizowaną wersję kodu źródłowego dla narzędzia kontraktów kodu z [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Pobierz informacje znajdują się w dolnej części strony.|
|Zakres|Pomocnicza|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

