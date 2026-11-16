
# ==========================================================
# PROGETTO: ANALISI DELLE VENDITE IN UNA CATENA DI NEGOZI
# ==========================================================

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt


# ==========================================================
# PARTE 1 - CREAZIONE DEL DATASET CSV
# ==========================================================

print("\n========== PARTE 1 - CREAZIONE DATASET ==========")

# Creazione dei dati di vendita
dati_vendite = {

    "Data": [
        "2023-09-01", "2023-09-01", "2023-09-01",
        "2023-09-02", "2023-09-02", "2023-09-02",
        "2023-09-03", "2023-09-03", "2023-09-03",
        "2023-09-04", "2023-09-04", "2023-09-04",
        "2023-09-05", "2023-09-05", "2023-09-05",
        "2023-09-06", "2023-09-06", "2023-09-06",
        "2023-09-07", "2023-09-07", "2023-09-07",
        "2023-09-08", "2023-09-08", "2023-09-08",
        "2023-09-09", "2023-09-09", "2023-09-09",
        "2023-09-10", "2023-09-10", "2023-09-10",
        "2023-09-11", "2023-09-11", "2023-09-11",
        "2023-09-12", "2023-09-12", "2023-09-12",
        "2023-09-13", "2023-09-13", "2023-09-13",
        "2023-09-14"
    ],

    "Negozio": [
        "Milano", "Roma", "Napoli",
        "Milano", "Roma", "Torino",
        "Napoli", "Milano", "Roma",
        "Torino", "Napoli", "Milano",
        "Roma", "Torino", "Napoli",
        "Milano", "Roma", "Torino",
        "Napoli", "Milano", "Roma",
        "Torino", "Napoli", "Milano",
        "Roma", "Torino", "Napoli",
        "Milano", "Roma", "Torino",
        "Napoli", "Milano", "Roma",
        "Torino", "Napoli", "Milano",
        "Roma", "Torino", "Napoli",
        "Milano"
    ],

    "Prodotto": [
        "Smartphone", "Laptop", "TV",
        "Laptop", "Smartphone", "Tablet",
        "TV", "Smartphone", "Laptop",
        "Tablet", "Smartphone", "TV",
        "Laptop", "Smartphone", "Tablet",
        "TV", "Laptop", "Smartphone",
        "Tablet", "TV", "Smartphone",
        "Laptop", "Tablet", "Smartphone",
        "TV", "Laptop", "Smartphone",
        "Tablet", "Smartphone", "TV",
        "Laptop", "Smartphone", "Tablet",
        "TV", "Laptop", "Smartphone",
        "Tablet", "TV", "Laptop",
        "Smartphone"
    ],

    "Quantità": [
        5, 2, 3, 4, 6, 3, 2, 7, 3, 4,
        5, 2, 4, 6, 3, 2, 5, 4, 6, 3,
        8, 2, 5, 4, 3, 6, 7, 2, 4, 5,
        3, 9, 2, 4, 5, 6, 3, 4, 2, 7
    ],

    "Prezzo_unitario": [
        499.99, 899.99, 699.99,
        850.00, 520.00, 350.00,
        750.00, 480.00, 920.00, 330.00,
        510.00, 720.00, 880.00, 495.00,
        340.00, 680.00, 910.00, 505.00,
        320.00, 730.00, 490.00, 950.00,
        360.00, 515.00, 710.00, 890.00,
        345.00, 500.00, 930.00, 740.00,
        870.00, 485.00, 355.00, 760.00,
        900.00, 525.00, 340.00, 695.00,
        920.00, 510.00
    ]
}

# Creazione del DataFrame iniziale
df_iniziale = pd.DataFrame(dati_vendite)

# Salvataggio del dataset in formato CSV
df_iniziale.to_csv(
    "vendite.csv",
    index=False,
    encoding="utf-8-sig"
)

print("File vendite.csv creato correttamente.")
print("Numero di vendite inserite:", len(df_iniziale))


# ==========================================================
# PARTE 2 - IMPORTAZIONE CON PANDAS
# ==========================================================

print("\n========== PARTE 2 - IMPORTAZIONE CON PANDAS ==========")

# Importazione del file CSV
df = pd.read_csv("vendite.csv")

# Visualizzazione delle prime 5 righe
print("\nPRIME 5 RIGHE DEL DATASET:")
print(df.head())

# Numero di righe e colonne
print("\nDIMENSIONI DEL DATASET:")
print(df.shape)

# Informazioni generali
print("\nINFORMAZIONI GENERALI:")
df.info()

# Conversione della colonna Data in formato datetime
df["Data"] = pd.to_datetime(df["Data"])


# ==========================================================
# PARTE 3 - ELABORAZIONI CON PANDAS
# ==========================================================

print("\n========== PARTE 3 - ELABORAZIONI CON PANDAS ==========")

# Creazione della colonna Incasso
df["Incasso"] = df["Quantità"] * df["Prezzo_unitario"]

print("\nDATASET CON LA COLONNA INCASSO:")
print(df.head())

# Incasso totale di tutta la catena
incasso_totale = df["Incasso"].sum()

print("\nINCASSO TOTALE DELLA CATENA:")
print(round(incasso_totale, 2), "euro")

# Incasso medio per negozio
incasso_medio_negozio = df.groupby(
    "Negozio"
)["Incasso"].mean()

print("\nINCASSO MEDIO PER NEGOZIO:")
print(incasso_medio_negozio.round(2))

# I 3 prodotti più venduti in termini di quantità
prodotti_piu_venduti = df.groupby(
    "Prodotto"
)["Quantità"].sum().sort_values(ascending=False).head(3)

print("\nI 3 PRODOTTI PIÙ VENDUTI:")
print(prodotti_piu_venduti)

# Incasso medio raggruppato per negozio e prodotto
incasso_negozio_prodotto = df.groupby(
    ["Negozio", "Prodotto"]
)["Incasso"].mean()

print("\nINCASSO MEDIO PER NEGOZIO E PRODOTTO:")
print(incasso_negozio_prodotto.round(2))


# ==========================================================
# PARTE 4 - ELABORAZIONI CON NUMPY
# ==========================================================

print("\n========== PARTE 4 - ELABORAZIONI CON NUMPY ==========")

# Estrazione della colonna Quantità come array NumPy
q = df["Quantità"].to_numpy()

# Calcolo delle statistiche
media = np.mean(q)
minimo = np.min(q)
massimo = np.max(q)
deviazione_standard = np.std(q)

# Numero di vendite sopra la media
vendite_sopra_media = np.sum(q > media)

# Percentuale di vendite sopra la media
percentuale_sopra_media = (
    vendite_sopra_media / len(q)
) * 100

print("\nSTATISTICHE DELLE QUANTITÀ VENDUTE:")
print("Media:", round(media, 2))
print("Minimo:", minimo)
print("Massimo:", massimo)
print("Deviazione standard:", round(deviazione_standard, 2))
print("Vendite sopra la media:", vendite_sopra_media)
print("Percentuale sopra la media:", round(percentuale_sopra_media, 2), "%")


# Creazione di un array NumPy 2D
# Prima colonna = Quantità
# Seconda colonna = Prezzo unitario

array_vendite = df[
    ["Quantità", "Prezzo_unitario"]
].to_numpy()

print("\nARRAY NUMPY 2D:")
print(array_vendite)

# Calcolo dell'incasso per ogni riga
incassi_numpy = array_vendite[:, 0] * array_vendite[:, 1]

print("\nINCASSI CALCOLATI CON NUMPY:")
print(incassi_numpy)

# Confronto con la colonna Incasso del DataFrame
incassi_pandas = df["Incasso"].to_numpy()

confronto = np.allclose(
    incassi_numpy,
    incassi_pandas
)

print("\nVERIFICA DELLA CORRETTEZZA:")
if confronto:
    print("I risultati NumPy e Pandas coincidono.")
else:
    print("I risultati NumPy e Pandas non coincidono.")


# ==========================================================
# PARTE 5 - VISUALIZZAZIONI CON MATPLOTLIB
# ==========================================================

print("\n========== PARTE 5 - VISUALIZZAZIONI ==========")


# GRAFICO 1 - INCASSO TOTALE PER NEGOZIO

incasso_negozio = df.groupby(
    "Negozio"
)["Incasso"].sum()

plt.figure(figsize=(9, 6))

incasso_negozio.plot(kind="bar")

plt.title("Incasso totale per negozio")
plt.xlabel("Negozio")
plt.ylabel("Incasso in euro")
plt.xticks(rotation=0)
plt.tight_layout()

plt.show()


# GRAFICO 2 - PERCENTUALE DI INCASSI PER PRODOTTO

incasso_prodotto = df.groupby(
    "Prodotto"
)["Incasso"].sum()

plt.figure(figsize=(8, 8))

plt.pie(
    incasso_prodotto.values,
    labels=incasso_prodotto.index,
    autopct="%1.1f%%",
    startangle=90
)

plt.title("Percentuale di incassi per prodotto")
plt.tight_layout()

plt.show()


# GRAFICO 3 - ANDAMENTO GIORNALIERO DEGLI INCASSI

incasso_giornaliero = df.groupby(
    "Data"
)["Incasso"].sum()

plt.figure(figsize=(10, 6))

plt.plot(
    incasso_giornaliero.index,
    incasso_giornaliero.values,
    marker="o"
)

plt.title("Andamento giornaliero degli incassi")
plt.xlabel("Data")
plt.ylabel("Incasso in euro")
plt.xticks(rotation=45)
plt.grid(True)
plt.tight_layout()

plt.show()


# ==========================================================
# PARTE 6 - ANALISI AVANZATA
# ==========================================================

print("\n========== PARTE 6 - ANALISI AVANZATA ==========")

# Dizionario che associa i prodotti alle categorie

categorie_prodotti = {

    "Smartphone": "Informatica",
    "Laptop": "Informatica",
    "Tablet": "Informatica",

    "TV": "Elettrodomestici"
}

# Creazione della nuova colonna Categoria
df["Categoria"] = df["Prodotto"].map(
    categorie_prodotti
)

print("\nDATASET CON LA COLONNA CATEGORIA:")
print(df.head())

# Incasso totale per categoria
incasso_categoria = df.groupby(
    "Categoria"
)["Incasso"].sum()

print("\nINCASSO TOTALE PER CATEGORIA:")
print(incasso_categoria.round(2))

# Quantità media venduta per categoria
quantita_media_categoria = df.groupby(
    "Categoria"
)["Quantità"].mean()

print("\nQUANTITÀ MEDIA VENDUTA PER CATEGORIA:")
print(quantita_media_categoria.round(2))

# Salvataggio del DataFrame aggiornato
df.to_csv(
    "vendite_analizzate.csv",
    index=False,
    encoding="utf-8-sig"
)

print("\nFile vendite_analizzate.csv salvato correttamente.")


# ==========================================================
# PARTE 7 - ESTENSIONI
# ==========================================================

print("\n========== PARTE 7 - ESTENSIONI ==========")


# Funzione che restituisce i primi N prodotti
# ordinati in base all'incasso totale

def top_n_prodotti(n):

    risultati = df.groupby(
        "Prodotto"
    )["Incasso"].sum().sort_values(
        ascending=False
    )

    return risultati.head(n)


# Esempio: primi 3 prodotti per incasso totale
print("\nTOP 3 PRODOTTI PER INCASSO TOTALE:")

print(top_n_prodotti(3))


# GRAFICO COMBINATO:
# BARRE = INCASSO MEDIO PER CATEGORIA
# LINEA = QUANTITÀ MEDIA VENDUTA

# Calcolo dell'incasso medio per categoria
incasso_medio_categoria = df.groupby(
    "Categoria"
)["Incasso"].mean()

# Calcolo della quantità media per categoria
quantita_media_categoria = df.groupby(
    "Categoria"
)["Quantità"].mean()

# Creazione del grafico
fig, ax1 = plt.subplots(figsize=(9, 6))

# Grafico a barre
ax1.bar(
    incasso_medio_categoria.index,
    incasso_medio_categoria.values,
    alpha=0.7,
    label="Incasso medio"
)

ax1.set_xlabel("Categoria")
ax1.set_ylabel("Incasso medio in euro")
ax1.set_title("Incasso medio e quantità media per categoria")

# Creazione del secondo asse verticale
ax2 = ax1.twinx()

# Grafico a linee
ax2.plot(
    quantita_media_categoria.index,
    quantita_media_categoria.values,
    marker="o",
    label="Quantità media"
)

ax2.set_ylabel("Quantità media venduta")

# Unione delle legende
linee1, etichette1 = ax1.get_legend_handles_labels()
linee2, etichette2 = ax2.get_legend_handles_labels()

ax1.legend(
    linee1 + linee2,
    etichette1 + etichette2,
    loc="upper right"
)

plt.tight_layout()
plt.show()


# ==========================================================
# FINE DEL PROGETTO
# ==========================================================

print("\n========== PROGETTO COMPLETATO ==========")
print("Tutte le analisi sono state eseguite correttamente.")
