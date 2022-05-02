Table users {
  id int(15) [pk, increment] // auto-increment
  type varchar(100)
  full_name varchar(100)
  wallet_address varchar(100)
  nft_address varchar(100)
  passward varchar(100)
  email_address varchar(100)
  address varchar(100)
  organization varchar(100)
  created_at timestamp
}

Table donation_record {
  id int(15) [pk, increment] // auto-increment
  user_id int(15)
  transaction_address varchar(100)
  product_type varchar(100)
  product_quantity varchar(10)
  created_at timestamp
}

Table color_pencil_maker_record {
  id int(15) [pk, increment] // auto-increment
  partner_id int(15)
  transaction_address varchar(100)
  donation_record_id int(15)
  donation_type varchar(100)
  donation_quantity varchar(10)
  transfer_date varchar(100)
  cost varchar(100) //we may cover the cost of tranfer
  created_at timestamp
}

Table color_pencil_production_record {
  id int(15) [pk, increment] // auto-increment
  partner_id int(15)
  transaction_address varchar(100)
  new_product_type varchar(100)
  new_product_quantity varchar(10)
  cost varchar(10)
  created_at timestamp
}

Table color_pencil_distribution_record {
  id int(15) [pk, increment] // auto-increment
  color_pencil_production_id int(15)
  transaction_address varchar(100)
  product_quantity varchar(10)
  receiver_id int(15)
  distribution_date timestamp
  created_at timestamp
}

Table color_pencil_sale_record {
  id int(15) [pk, increment] // auto-increment
  color_pencil_production_id int(15)
  transaction_address varchar(100)
  sale_quantity varchar(10)
  sale_price varchar(100)
  sale_date timestamp
  created_at timestamp
}

Table color_pencil_sale_profit_record {
  id int(15) [pk, increment] // auto-increment
  color_pencil_sale_record_id int(15)
  transaction_address varchar(100)
  sale_profit varchar(100)
  created_at timestamp
}

Table color_pencil_sale_profit_tranfer_record {
  id int(15) [pk, increment] // auto-increment
  color_pencil_sale_profit_record_id int(15)
  transaction_address varchar(100)
  receiver_id int(15)
  tranfer_date timestamp
  created_at timestamp
}

Ref: users.id < donation_record.id
Ref: users.id < color_pencil_sale_profit_tranfer_record.receiver_id
Ref: color_pencil_sale_profit_record.id > color_pencil_sale_profit_tranfer_record.id
Ref: color_pencil_sale_profit_record.color_pencil_sale_record_id > color_pencil_sale_record.id
Ref: color_pencil_sale_record.id > color_pencil_production_record.id
Ref: color_pencil_distribution_record.id > color_pencil_production_record.id
Ref: color_pencil_distribution_record.receiver_id > users.id
Ref: color_pencil_production_record.partner_id > users.id
Ref: color_pencil_maker_record.partner_id > users.id
Ref: color_pencil_maker_record.donation_record_id > donation_record.id
Ref: donation_record.user_id > users.id


