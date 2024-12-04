CREATE TABLE client(
   Id_client INT AUTO_INCREMENT,
   nom VARCHAR(50) ,
   prenom VARCHAR(50) ,
   adresse_facturation VARCHAR(50) ,
   photo_identite VARCHAR(50) ,
   PRIMARY KEY(Id_client)
);

CREATE TABLE place(
   Id_place INT AUTO_INCREMENT,
   nom_place VARCHAR(50) ,
   prix_base DECIMAL(15,2)   NOT NULL,
   prix_jour DECIMAL(15,2)   NOT NULL,
   corps_mort BOOLEAN,
   PRIMARY KEY(Id_place)
);

CREATE TABLE bateau(
   Id_bateau INT AUTO_INCREMENT,
   matricule VARCHAR(50) ,
   type_bateau INT NOT NULL,
   Id_client INT NOT NULL,
   PRIMARY KEY(Id_bateau),
   FOREIGN KEY(Id_client) REFERENCES client(Id_client)
);

CREATE TABLE facture(
   Id_facture INT AUTO_INCREMENT,
   PRIMARY KEY(Id_facture)
);

CREATE TABLE Abonnement(
   Id_Abonnement INT AUTO_INCREMENT,
   dateDeb DATE NOT NULL,
   dateFn DATE NOT NULL,
   type_abonnement VARCHAR(50) ,
   Id_place INT NOT NULL,
   Id_bateau INT NOT NULL,
   PRIMARY KEY(Id_Abonnement),
   UNIQUE(Id_place),
   FOREIGN KEY(Id_place) REFERENCES place(Id_place),
   FOREIGN KEY(Id_bateau) REFERENCES bateau(Id_bateau)
);

CREATE TABLE service(
   Id_service INT AUTO_INCREMENT,
   nom VARCHAR(50) ,
   prix VARCHAR(50) ,
   PRIMARY KEY(Id_service)
);

CREATE TABLE UTILISE(
   Id_Abonnement INT,
   Id_service INT,
   PRIMARY KEY(Id_Abonnement, Id_service),
   FOREIGN KEY(Id_Abonnement) REFERENCES Abonnement(Id_Abonnement),
   FOREIGN KEY(Id_service) REFERENCES service(Id_service)
);
